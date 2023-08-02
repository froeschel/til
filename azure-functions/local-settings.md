# Local settings file

When developing local always make sure that the file ``` local.settings.json ```  has set the  ```Copy to Output Directory ``` property to ```Copy always```. During local development on function runtime 4 I had problems that settings could not be read if the setting was not set correctly. 