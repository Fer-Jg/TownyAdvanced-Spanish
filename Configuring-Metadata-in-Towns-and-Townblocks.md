The Towny API has a list of properties already hooked to towns and townblocks that are editable by Towny plugin developers. While a lot of these are useful in the context of Towny, as an independent plugin developer, you may want to store other custom data within towns or townblocks. This is the purpose of metadata.

### Why use Metadata as opposed to storing data within your plugin?
* Data not stored in the Towny plugin is decentralized which makes it hard for other devs to see and manipulate your stored data, this is especially problematic if another plugin depends on data from the plugin you are developing. Towny metadata is centralized thus allowing for easy access via documentation, and key-names.
* If your plugin requires external data on towns/townblocks, developing a backend to deal with it, can be cumbersome and time intensive.
* Metadata allows for custom fields in Towns and Townblocks like the ones already included, ie: pvp, explosions, residents.

### Example plugins using Metadata
Check out [Plugins using Metadata](https://github.com/TownyAdvanced/Towny/wiki/Plugins-using-the-Towny-API#plugins-using-metadata)

### How to use the Metadata within the TownyAPI
The API uses a data field system for storing metadata.

#### Anatomy of Data Fields
- `CustomDataField`
  - `IntegerDataField`
  - `StringDataField`
  - `BooleanDataField`
  - `DecimalDataField`

Each of the data field hold a specific type of data that can be properly deserialized when towny loads.

#### Registering custom data with your plugin.

1) Make sure that your plugin depends on Towny, you can do this by adding this to your plugin.yml:
     ```
     depends:
       - Towny
     ```
2) Add Towny as a dependency to Maven [as described here.](https://github.com/TownyAdvanced/Towny/wiki/TownyAPI#getting-started-with-towny-and-your-ide)
3) Register data field in `onLoad()` function:
```java
public class Main extends JavaPlugin {

    private File blockFile = new File(getDataFolder(), "blockvalues.yml");
    private FileConfiguration blockConfig = YamlConfiguration.loadConfiguration(blockFile);

    private static String keyname = "unique"; // This key must be unique to your plugin.
    private static int defaultVal = 0; // This is the default value your data field will have whenever its added to an object.
    private static IntegerDataField myCustomIntegerField = new IntegerDataField(keyname, defaultVal);

    // Called when the plugin first loads.
    @Override
    public void onLoad() {
        // Try to register the data field.
        try {
            TownyAPI.getInstance().registerCustomDataField(myCustomIntegerField);
        } catch (KeyAlreadyRegisteredException e) {
            getLogger().warning(e.getMessage()); // A flag with the same key name already exists try again
        }

        getLogger().info("Flag successfully registered!");
    }
    
    public static IntegerDataField getMyCustomIntegerField() {
        return myCustomIntegerField;
    }
}
```
     
#### Attaching metadata to Towns and Town blocks
```java
// For townblock objects
townblock.addMetaData(myCustomIntegerField);

// For town objects
town.addMetaData(myCustomIntegerField);
```

Alternatively, if you want your metadata available to all towns by default you could loop through all of the objects on initialization and add the custom data.


#### Retrieving and modifying custom data fields
```java
public void manipulateData(TownBlock townBlock) {
        IntegerDataField myField = null;

        // Search for the custom data in the given townblock.
        for (CustomDataField cdf : townBlock.getMetadata()) {
            if (cdf.equals(myCustomIntegerField)) { // Use the static field
                myField = (IntegerDataField)cdf;
            }
        }

        // Set the value to the retrieved key.
        if (myField != null) {
            myField.setValue(10);
        }
}
```

With that you should be able to edit, add and change metadata.

Full Example File:
```java
public class Main extends JavaPlugin {

    private File blockFile = new File(getDataFolder(), "blockvalues.yml");
    private FileConfiguration blockConfig = YamlConfiguration.loadConfiguration(blockFile);

    private static String keyname = "unique"; // This key must be unique to your plugin.
    private static int defaultVal = 0; // This is the default value your data field will have whenever its added to an object.
    private static IntegerDataField myCustomIntegerField = new IntegerDataField(keyname, defaultVal);
    

    // Called when the plugin first loads.
    @Override
    public void onLoad() {
        // Try to register the data field.
        try {
            TownyAPI.getInstance().registerCustomDataField(getMyCustomIntegerField());
        } catch (KeyAlreadyRegisteredException e) {
            getLogger().warning(e.getMessage()); // A flag with the same key name already exists try again
        }

        getLogger().info("Flag successfully registered!");
    }

    public static IntegerDataField getMyCustomIntegerField() {
        return myCustomIntegerField;
    }

    public void manipulateData(TownBlock townBlock) {
        IntegerDataField myField = null;

        // Search for the custom data in the given townblock.
        for (CustomDataField cdf : townBlock.getMetadata()) {
            if (cdf.equals(getMyCustomIntegerField())) {
                myField = (IntegerDataField)cdf;
            }
        }

        // Set the value to the retrieved key.
        if (myField != null) {
            myField.setValue(10);
        } else {
            // Key is not part of town block.
        }
    }

}
```


