# Training---Add-An-Admin-Menu-Link-To-Your-Custom-Plugin

Database Structure
  Description: This table inludes all the link records to access installed plugins in the website’s admin through the go.php link structure
  Storage Engine: InnoDB
  Collation: utf8_unicode_ci
  Table Name: plugin_records
  Columns: 
        1. plugin_record_id (PRIMARY)
        2. active: 0 or 1 for active or inactive. Inactive records will not be taken into account for display
        3. variable_name (UNIQUE)
        nick_name
        4. Name that will be shown to the admin
        5. link_url
        6. Url to access. EG: /admin/go.php?widget=XXXXXXXXXXX


How to Create / Add a Plugin to the "Plugins" Menu Item in the Admin Area
    Login to the website's directory database
    If the `plugin_records` table does not exist, run the following SQL to create the plugin_records table:

CREATE TABLE IF NOT EXISTS `plugin_records` (
      `plugin_record_id` bigint(20) NOT NULL AUTO_INCREMENT,
      `active` tinyint(1) NOT NULL,
      `variable_name` varchar(80) COLLATE utf8_unicode_ci NOT NULL,
      `nick_name` varchar(80) COLLATE utf8_unicode_ci NOT NULL,
      `link_url` varchar(100) COLLATE utf8_unicode_ci NOT NULL,
      PRIMARY KEY (`plugin_record_id`),
      UNIQUE KEY `variable_name` (`variable_name`)
    ) ENGINE=InnoDB  DEFAULT CHARSET=utf8 COLLATE=utf8_unicode_ci COMMENT='This table has all the link records to access widgets with the go.php file' AUTO_INCREMENT=1;
    
    
    Insert the information for your plugin link as required following the column structure indicated above 


The link_url value is a complete link instead of the widget name because some special cases may require sending GET parameters from the start. 
If you want to add a new record on the database you need to do it manually, there is not an UI to add records to this new table. 
