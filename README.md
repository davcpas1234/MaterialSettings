#MaterialSettings

The open repository with a global support for Android 5 Toolbar within any Settings Activity (`PreferenceActivity`).

##Important Compatibility
###Gingerbread

In order to handle nested `PreferenceScreens` correctly `onConfigurationChanged()` must be overriden in your `SettingsActivity` as below:

```java
    public void onConfigurationChanged(Configuration newConfig) {
        super.onConfigurationChanged(newConfig);
    }
```

and so this code is called, add the following to your `SettingsActivity` declaration in your `AndroidManifest.xml`:
```xml
android:configChanges="keyboard|keyboardHidden|orientation|screenSize"
```

Thanks to @hclemens for indentifying this.