# Php Snippent 
<!-- php built-in function snippents -->
```php 
    /* array_map */
    
    $a = [1,2,3];

    $sqtr_a = array_map(function($x){
        return $x*$x;
    },$a);

    /* output :- [ 1,4,9] */

```


#Magento 2 Snippents


# Magento Snippents
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
INSERT INTO `customer_entity_int` (`attribute_id`, `entity_id`, `value`) VALUES ( 282, 153, 3522 ) ON DUPLICATE KEY UPDATE `value`= 3522;
```
