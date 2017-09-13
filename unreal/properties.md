# Properties
[Wiki](../readme.md)/[Unreal](readme.md)/Properties

## Declaration

```c++
UPROPERTY([specifier, specifier, ...], [meta=(key=value, key=value, ...)])
Type VariableName;
```

## Garbage Collection
Any Object that has at least one valid pointer stored inside a UPROPERTY will not be Garbage Collected (GC). Non-UPROPERTY variables will not be counted by the GC system.

## Property Specifiers

### Multicast Delegates
* `BlueprintAssignable`

MC Delegates only. Property should be exposed for assigning in blueprints.

* `BlueprintCallable`

Multicast Delegates only. Property should be exposed for calling in blueprint code

* `BlueprintAuthorityOnly`

MC Delegates only. This delegate accepts (only in blueprint) only events with BlueprintAuthorityOnly.

### Serialization/Memory allocation/GC

* `Config`

Property should be loaded/saved to ini file as permanent profile

* `GlobalConfig`

Same as above but load config from base class, not subclass.

* `Localized`

Property should be loaded as localizable text. Implies ReadOnly.

* `Transient`

Property is transient: shouldn't be saved, zero-filled at load time. Opposite of the SaveGame specifier.

* `DuplicateTransient`

Property should always be reset to the default value during any type of duplication (copy/paste, binary duplication, etc.)

* `NonPIETransient`

Property should always be reset to the default value during any type of duplication (copy/paste, binary duplication, etc.)

* `Ref`

Value is copied out after function call. Only valid on function param declaration.
Note This is a UPARAM specifier; not a UPROPERTY specifier.

* `SaveGame`

Property should be serialized for save game. Opposite of the Transient specifier.

* `TextExportTransient`

Property shouldn't be exported to text format (e.g. copy/paste)

### Editor Display

* `AssetRegistrySearchable`

The AssetRegistrySearchable keyword indicates that this property and it's value will be automatically added to the asset registry for any asset class instances containing this as a member variable. It is not legal to use on struct properties or parameters.

* `Category`

Specifies the category of the property within the Editor. Supports sub-categories separated by "|".

Example
```c++
UPROPERTY(Category = "CategoryName")

UPROPERTY(Category = "Category|SubCategory")
```
* `DisplayName` _[Meta]_

Sets the display name for the property in the editor. The default value is the variable name with a space before each capital letter beyond the first. For example 'MyVariableName' would display as 'My Variable Name'.

Example
```c++
UPROPERTY(meta = (DisplayName = "My Display Name"))
```
Note Boolean variables with names that start with a lowercase "b" will be culled by default within the Editor

* `NoClear`

Hide clear (and browse) button in the editor.

* `SimpleDisplay`

Properties appear visible by default in a details panel

* `AdvancedDisplay`

Moves the property into the Advanced dropdown in the Details panel within the Editor.

Note Does not appear to work within property subcategories as of 4.12.5

* `AllowAbstract` _[Meta]_

Used for FStringClassReference properties. Indicates whether abstract class types should be shown in the class picker.

* `AllowedClasses` _[Meta]_

Used for FStringAssetReference properties. Comma delimited list that indicates the class type(s) of assets to be displayed in the asset picker.

* `AllowPreserveRatio` _[Meta]_

Used for FVector properties. It causes a ratio lock to be added when displaying this property in details panels.

* `ArrayClamp`

Used for integer properties. Clamps the valid values that can be entered in the UI to be between 0 and the length of the array specified.

* `ClampMin` _[Meta]_

Used for float and integer properties. Specifies the minimum value that may be entered for the property.

Example
```c++
UPROPERTY(meta = (ClampMin = 0)
int32 Clamp;
```
Note Does not work with containers, such as TArray<float>

* `ClampMax` _[Meta]_

Used for float and integer properties. Specifies the maximum value that may be entered for the property.

Example
```c++
UPROPERTY(meta = (ClampMax = 10.5)
float Clamp;
```
Note Does not work with containers, such as TArray<float>

* `DisplayThumbnail` _[Meta]_

Indicates that the property is an asset type and it should display the thumbnail of the selected asset.

* `EditCondition` _[Meta]_

Specifies a boolean property that is used to indicate whether editing of this property is allowed within the editor.

Example
```c++
UPROPERTY(BlueprintReadWrite, EditAnywhere)
bool bAllowEdit;

UPROPERTY(BlueprintReadWrite, EditAnywhere, meta = (EditCondition = bAllowEdit))
int32 EditMe;
```

* `ExactClass` _[Meta]_

Used for FStringAssetReference properties in conjunction with AllowedClasses. Indicates whether only the exact classes specified in AllowedClasses can be used or whether subclasses are valid.

* `HideAlphaChannel` _[Meta]_

Used for FColor and FLinearColor properties. Indicates that the Alpha property should be hidden when displaying the property widget in the details.

* `IsBlueprintBaseOnly` _[Meta]_

Used for FStringClassReference properties. Indicates whether only blueprint classes should be shown in the class picker.

* `OnlyPlaceable` _[Meta]_

Used for Subclass properties. Indicates whether only placeable classes should be shown in the class picker.

* `MakeEditWidget` _[Meta]_

When used with certain objects such as an FVector, you get to use an "edit widget" within the editor to transform the object in space.

* `MakeStructureDefaultValue` _[Meta]_

For properties in a structure indicates the default value of the property in a blueprint make structure node.

* `MetaClass` _[Meta]_

Used FStringClassReference properties. Indicates the parent class that the class picker will use when filtering which classes to display.

* `MultiLine` _[Meta]_

Used for FString and FText properties. Indicates that the edit field should be multi-line, allowing entry of newlines.

Usage: "meta=(MultiLine=true)"

* `NoElementDuplicate` _[Meta]_

Used for array properties. Indicates that the duplicate icon should not be shown for entries of this array in the property panel.

* `NoSpinbox` _[Meta]_

Used for integer and float properties. Indicates that the spin box element of the number editing widget should not be displayed.

* `FilePathFilter` _[Meta]_

Used by FFilePath properties. Indicates the path filter to display in the file picker.

* `RelativePath` _[Meta]_

Used by FDirectoryPath properties.

* `RelativeToGameContentDir` _[Meta]_

Used by FDirectoryPath properties.

* `ShowOnlyInnerProperties` _[Meta]_

Used for struct properties. The properties of the struct are shown directly in the details panel instead of having the need to expand them to show them.

* `UIMin` _[Meta]_

Used for float and integer properties. Specifies the lowest that the value slider should represent.

* `UIMax` _[Meta]_

Used for float and integer properties. Specifies the highest that the value slider should represent.

### Blueprint Access

* `BlueprintReadOnly`

This property can be read by blueprints, but not modified.

* `BlueprintReadWrite`

This property can be read or written from a blueprint.

* `EditFixedSize`

Indicates that elements of an array can be modified in Editor, but its size cannot be changed.

Note Static arrays of containers, such as TArray, are not allowed. Use dynamic arrays.

Note May not work properly with container arrays of Structs. Mine were not editable. 4.12.5

* `EditInline`

Edit this object reference inline in the editor.

* `NonTransactional`

Changes to this variable value will not be included in the editor's undo/redo history.

* `Instanced`

Property is a component reference. Implies EditInline and Export.

* `EditAnywhere`

Indicates that this property can be edited via property windows, archetypes and instances within the Editor.

* `EditInstanceOnly`

Indicates that this property can be edited by property windows, but only on instances, not on archetypes

* `EditDefaultsOnly`

Indicates that this property can be edited by property windows, but only on archetypes. This operator is incompatible with the Visible* specifiers.

* `VisibleAnywhere`

Indicates that this property is visible in property windows, but cannot be edited at all

* `VisibleInstanceOnly`

Indicates that this property is only visible in property windows for instances, not for archetypes, and cannot be edited

* `VisibleDefaultsOnly`

Indicates that this property is only visible in property windows for archetypes, and cannot be edited

### Networking

* `Replicated`

Property is relevant to network replication.

* `ReplicatedUsing`

Property will be configured for replication. The provided function is called only when the replicated property is received via replication.

Example
```c++
UPROPERTY(ReplicatedUsing = OnRep_ReplicatedVar)
int32 ReplicatedVar;
void OnRep_ReplicatedVar();

//or
void OnRep_ReplicatedVar(int32 OldValue);
```

* `RepRetry`

Retry replication of this property if it fails to be fully sent (e.g. object references not yet available to serialize over the network)

* `NotReplicated`

Skip replication (only for struct members and parameters in service request functions).

## ???

* `Export`

Object property can be exported with it's owner.

* `Interp`

Interpolatable property for use with matinee. Always user-settable in the editor.

* `ExposeFunctionCategories` _[Meta]_

[Undocumented]

* `ExposeOnSpawn` _[Meta]_

Specifies whether the property should be exposed on a Spawn Actor for the class type.

Example	
```c++
UPROPERTY(BlueprintReadWrite, meta = (ExposeOnSpawn)
```

* `FixedIncrement` _[Meta]_

[Undocumented]

* `ForceRebuildProperty` _[Meta]_

[Undocumented]

* `Multiple` _[Meta]_

[Undocumented]

* `SliderExponent` _[Meta]_

[Undocumented]
