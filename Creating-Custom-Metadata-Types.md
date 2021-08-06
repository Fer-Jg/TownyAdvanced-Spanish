There may be some cases where a Towny-provided data field does not satisfy a specific use-case of your project. In these cases, Towny provides an API to register and utilize custom data field objects instead.

There are two essential phases in creating a custom data field.
1. New implementation of the `CustomDataField` base class.
2. Creating a deserializer to parse storage into instances of the `CustomDataField` implementation.

To demonstrate how to perform these two phases, we will create a UUIDListDataField object that will be able to store a list of UUIDs on TownyObjects.

### Implementing the `CustomDataField` class
The goal of this phase is to create a new implementation of the [`CustomDataField` class](https://github.com/TownyAdvanced/Towny/blob/master/src/com/palmergames/bukkit/towny/object/metadata/CustomDataField.java).

The first thing to do is to create a class `UUIDListDataField` that extends the `CustomDataField` class with the type `List<UUID>`. Each implementation of a data field is represented in storage by a unique string known as the type ID. All of the Towny-provided type IDs are prefixed with `towny_`. It is suggested to prefix custom type IDs with the plugin name in order to avoid conflicts. 

We will now show the class implementation with comments to describe each step.
```java
// The CustomDatField class is a typed class that accepts a type parameter
// representing the type of the value to be stored.
// In this case, we are storing a list of UUIDs so our type parameter will be List<UUID>.
public class UUIDListDataField extends CustomDataField<List<UUID>> {

	// There are various constructors for a CustomDataField
	// Make sure to implement the ones that you will use in your plugin
	// because none of them will be available by default since they are all typed.
	public UUIDListDataField(String key, List<UUID> value, String label) {
		super(key, value, label);
	}
	
	// This constructor is HIGHLY recommended to be implemented since it will
	// be used in the deserializer.
	public UUIDListDataField(String key, List<UUID> value) {
		super(key, value);
	}

	// Like mentioned above, each CustomDataField implementation requires
	// a unique type ID.
	// It is recommended to create a static type ID method because the value will
	// be needed when registering the serializer and deserializer.
	// In this instance, the type id was prefixed with the name of the plugin, and then 
	// the "uuidlistdf" where "df" stands for DataField.
	@NotNull
	public static String typeID() {
		return "plugin_uuidlistdf";
	}
	
	// It's important to note that the typeID should be unique
	// to the class, and NOT the object instance. 
	// In other words, the type ID should be the same for all objects
	// of UUIDListDataField.
	@Override
	public @NotNull String getTypeID() {
		return typeID();
	}

	// If the datafield is globally registered, administrators
	// will be able to manually modify the value.
	// Thus we want to create a way to convert from a string
	// to a List<UUID>.
	// In this example, we will deliminate the UUIDs by a comma (',')
	@Override
	public void setValueFromString(String strValue) {
		// Suppose the administrator passed in a string
		// "7ef1fc4e-93d8-4278-98e8-200df0f3d5ec,3ce60fea-7070-4cff-8687-b3c37ac51f88"
		
		// The first thing to do would be to split the string by commas
		final String[] uuidStrSplit = strValue.split(",");
		
		// Next we want to parse each element as a UUID and store it in a list
		final List<UUID> uuidList = Arrays.stream(uuidStrSplit)
					   .map(UUID::fromString)
					   .collect(Collectors.toList());
		
		this.setValue(uuidList);
	}

	// This method should display the formatted 
	// list of UUIDs.
	// In this example, we will just display a comma-separated UUID-list.
	@Override
	public String displayFormattedValue() {
		final List<UUID> uuidList = this.getValue();
		if (uuidList == null || uuidList.isEmpty()) 
			return "<Empty>";
		
		return uuidList.stream()
			       .map(Objects::toString)
			       .collect(Collectors.joining(", "));
	}

	// This will detail how to serialize the object in storage.
	// In this example, the string will simply be a comma-separated list.
	@Override
	protected @Nullable String serializeValueToString() {
		List<UUID> uuidList = this.getValue();
		
		if (uuidList == null || uuidList.isEmpty())
			return null;
		
		return uuidList.stream()
				.map(Objects::toString)
				.collect(Collectors.joining(","));
	}

	// This method details how the object should be cloned.
	// In most custom cases, the only thing to really be concerned about
	// is making a deep-copy of the value.
	@Override
	public @NotNull CustomDataField<List<UUID>> clone() {
		// In this case, we want to make a copy of the UUID List
		final List<UUID> uuidList = this.getValue();
		List<UUID> copyList = null;
		
		if (uuidList != null)
			copyList = new ArrayList<>(uuidList);
		
		// getLabel() will never return null, but will instead return "nil" if no value set.
		// Thus, the label copy must manually be assigned to null if no label exists.
		final String copyLabel = hasLabel() ? getLabel() : null;
		
		return new UUIDListDataField(this.getKey(), copyList, copyLabel);
	}
}
```

### Creating a Deserializer for the DataField
This phase consists of creating a deserializer to parse the value from a string and registering it to Towny.

A deserializer will be the implementation of the [`DataFieldDeserializer` interface](https://github.com/TownyAdvanced/Towny/blob/master/src/com/palmergames/bukkit/towny/object/metadata/DataFieldDeserializer.java). The deserializer will be registered via `MetadataLoader#registerDeserializer(String, DataFieldDeserializer<?>)`.

*NOTE: Since the interface consists of a single-method (hence a functional interface), it can be implemented as a lambda argument to the `registerDeserializer` method.*

Here is an example implementation of the `DataFieldDeserializer` based on the example data field above.
```java
// The DataFieldDeserializer interface is also typed, however the type should
// be the custom Datafield implementation
public class UUIDListDFDeserializer implements DataFieldDeserializer<UUIDListDataField> {
	@Override
	public @Nullable UUIDListDataField deserialize(@NotNull String key, @Nullable String value) {
		// Convert the string value to a UUID List.
		// Based on how the object was serialized,
		// perform the reverse to deserialize the object.
		List<UUID> uuidList = null;
		
		// In this case, we serialized the object to a comma-separated list
		// so we can deserialize it the same way.
		
		// First we handle if the string is null
		if (value == null) {
			uuidList = new ArrayList<>();
		}
		// If there is an actual value then we can separate it
		else {
			uuidList = Arrays.stream(value.split(","))
				         .map(UUID::fromString)
				         .collect(Collectors.toCollection(ArrayList::new));
		}
		
		// Now we just create the instance of our custom data field object.
		return new UUIDListDataField(key, uuidList);
	}
}
```

Finally, we can register the data field deserializer in the enable method of our plugin:

```java
// Make sure that your plugin depends on Towny and loads after Towny.
public Plugin extends JavaPlugin {
     public void onEnable() {
            // ...
 	    MetadataLoader.getInstance()
		    .registerDeserializer(UUIDListDataField.typeID(), new UUIDListDFDeserializer());
     }
}
```

**IMPORTANT: All custom data field values will not be accessible when the server is loading. This is because Towny deserializes all metadata at the first tick of the server. So only access custom data field values after the server has been loaded.**

