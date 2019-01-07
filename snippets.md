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




#MySql 


**UPDATE & INSERT IN ONE QUERY:-**
[For More info.](https://dev.mysql.com/doc/refman/8.0/en/insert-on-duplicate.html)
```mysql
INSERT INTO `TABLE_NAME` (`COLUMN_NAME`) VALUES ( COLUMN_VALUE ) ON DUPLICATE KEY UPDATE `COLUMN_NAME`= COLUMN_VALUE;

/* get create table query of table */
SHOW TABLE CREATE TABLE_NAME;
```
