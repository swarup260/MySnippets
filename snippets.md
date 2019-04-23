# Php Snippent 
<!-- php built-in function snippents -->
```php 
    /* array_map */
    
    $a = [1,2,3];

    $sqtr_a = array_map(function($x){
        return $x*$x;
    },$a);

    /* output :- [ 1,4,9] */

    /* in_array */

    $a = ['a','b','c','d'];

    in_array('a',$a);
    /* output :- true if present else false */

```
### PHP Function 


```php

    /* optimize to load csv file using yield */
    function csvParser($filePath)
    {
        $file = fopen($filePath, "r") or die("unable to open");
        $headers = array_map('trim', fgetcsv($file, 4096));
        while (!feof($file)) {
            $row = array_map('trim', (array) fgetcsv($file, 4096));
            if (count($headers) !== count($row)) {
                continue;
            }
            $row = array_combine($headers, $row);
            yield $row;
        }
        fclose($file);
        return;
    }
    /* get the csv data */

    foreach(csvParser($filePath) as $value){
        print_r($value);
    }

```

#Magento 2 Snippents
___
 
### Routing Mechanism

index.php -> HTTP application -> FrontController -> Routing -> Controller processing -> etc


## routes.xml Boilerpate

```xml

<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/etc/routes.xsd">
    <router id="%routerId%">
        <route id="%routeId%" frontName="%frontName%">
            <module name="%moduleName%"/>
        </route>
    </router>
</config>
```

1. %routerId%   :- **specifies the name of the router in Magento.**  
2. %frontName%  :- **specifies the first segment after the base URL of a request.**
3. %moduleName% :- **specifies the name of your module.**

## basic observer 

1. create folder name observer in module folder .

```php

<?php 

namespace name;

use Magento\Framework\Event\ObserverInterface;

class className implements ObserverInterface
{
    public function execute(\Magento\Framework\Event\Observer $observer)
    {
        
    }
}


```

2. events.xml in module/etc/

```xml 

    <?xml version="1.0" encoding="UTF-8"?>
    <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="../../../../../../lib/internal/Magento/Framework/Event/etc/events.xsd">
    <event name="event_name">
        <observer name="vendorName_ModuleName_ObserverName" instance="class_namespace" />
    </event>
</config>

```

## CronTab 


```php 

<?php

namespace Mageplaza\HelloWorld\Cron;

class ClassName
{

	public function execute()
	{
        \\logic

	}
}

```


```xml 

<?xml version="1.0"?>
<!--
/**
 * Copyright © 2013-2017 Magento, Inc. All rights reserved.
 * See COPYING.txt for license details.
 */
-->
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="job_name" instance="classNamespce" method="execute">
            <schedule>30 2 * * *</schedule>
        </job>
    </group>
</config>

```

```
    * * * * * command to be executed
    | | | | |
    | | | | +----- Day of week (0 - 7) (Sunday=0 or 7)
    | | | +------- Month (1 - 12)
    | | +--------- Day of month (1 - 31)
    | +----------- Hour (0 - 23)
    +------------- Minute (0 - 59)

```


# MySql 


**UPDATE & INSERT IN ONE QUERY:-**
[For More info.](https://dev.mysql.com/doc/refman/8.0/en/insert-on-duplicate.html)
```mysql
INSERT INTO `TABLE_NAME` (`COLUMN_NAME`) VALUES ( COLUMN_VALUE ) ON DUPLICATE KEY UPDATE `COLUMN_NAME`= COLUMN_VALUE;

/* get create table query of table */
SHOW TABLE CREATE TABLE_NAME;
```


# JAVASCRIPT

**Prase the url to key,value pair**
```javascript
var vars = {};
    var parts = window.location.href.replace(/[?&]+([^=&]+)=([^&]*)/gi, function(m,key,value) {
        vars[key] = value;
    });
```