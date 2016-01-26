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
Full Example:
```xml
<activity
    android:name=".SettingsExampleActivity"
    android:label="@string/title_activity_settings_example"
    android:theme="@style/AppTheme.NoActionBar"
    android:configChanges="keyboard|keyboardHidden|orientation|screenSize">
    <intent-filter>
        <action android:name="android.intent.action.MAIN" />

        <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
</activity>
```

Thanks to [@hclemens](https://github.com/hclemens) for indentifying this.
