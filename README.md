### Deprecated (No Longer Developed)
This example is no longer maintained as Google have implemented the `AppCompatDelegate` class to implement Material Design in a `PreferenceActivity`. 

![Banner](https://raw.github.com/davcpas1234/MaterialSettings/master/media/app-banner.png)
# MaterialSettings

The open repository with a global support for Android 5 Toolbar within any Settings Activity (`PreferenceActivity`), compatible with API 10 and above.

## IMPORTANT - Compatibility
### Element Tinting
In order to mimic (material-like) element tinting on pre-L devices utilise the following code:
```java
@Override
public View onCreateView(String name, Context context, AttributeSet attrs) {
    // Allow super to try and create a view first
    final View result = super.onCreateView(name, context, attrs);
    if (result != null) {
        return result;
    }

    if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.JELLY_BEAN) {
        // If we're running pre-L, we need to 'inject' our tint aware Views in place of the
        // standard framework versions
        switch (name) {
            case "EditText":
                return new AppCompatEditText(this, attrs);
            case "Spinner":
                return new AppCompatSpinner(this, attrs);
            case "CheckBox":
                return new AppCompatCheckBox(this, attrs);
            case "RadioButton":
                return new AppCompatRadioButton(this, attrs);
            case "CheckedTextView":
                return new AppCompatCheckedTextView(this, attrs);
        }
    }

    return null;
}
```
>**Remember**: Import the appcompt-v7 library in your `app.gradle`:<br/>
>`compile 'com.android.support:appcompat-v7:22.2.0'`

### Gingerbread

In order to handle nested `PreferenceScreens` correctly `onConfigurationChanged()` must be overriden in your `SettingsActivity` as below:

```java
@Override
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

### Toolbar Shadow
To simulate the elevation of the Toolbar on pre-L devices, utilise the following code:

```xml
<android.support.design.widget.AppBarLayout
    android:layout_width="match_parent"
    android:layout_height="wrap_content">

   <android.support.v7.widget.Toolbar
       .../>

</android.support.design.widget.AppBarLayout>
```

>**Remember**: Import the Design library in your `app.gradle`:<br/>
>`compile 'com.android.support:design:22.2.0'`
