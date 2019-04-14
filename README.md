# systemsetup
res/xml/preference.xml
```
<?xml version="1.0" encoding="utf-8"?>
<PreferenceScreen xmlns:android="http://schemas.android.com/apk/res/android">
    <PreferenceCategory
        android:title="In-line preferences"
        android:key="pref_key_in">
        <CheckBoxPreference
            android:key="pref_key_cb"
            android:title="Checkbox preference"
            android:summary="This is a checkbox"
            android:defaultValue="true" />
    </PreferenceCategory>
    <PreferenceCategory
        android:title="Dialog-based preferences"
        android:key="pref_key_dialog">
        <EditTextPreference
            android:key="pref_key_et"
            android:title="Edit text preference"
            android:summary="An example that uses an edit text dialog">

        </EditTextPreference>
        <ListPreference
            android:key="pref_key_list"
            android:title="List preference"
            android:summary="An example that uses a list dialog"
            android:entries="@array/entry_list"
            android:entryValues="@array/values_list"
            android:dialogTitle="Choose one"
            ></ListPreference>
    </PreferenceCategory>
    <PreferenceCategory
        android:title="Launch preferences"
        android:key="pre_key_launch">
        <PreferenceScreen
            android:key="prf_key_p"
            android:title="Screan preference"
            android:summary="shows another screen of preferences">
            <CheckBoxPreference
                android:key="pref_key_cb2"
                android:title="Toggle preference"
                android:summary="preference that is on the next screen but same hierarchy"
                android:defaultValue="true" />
        </PreferenceScreen>
        <PreferenceScreen
            android:title="Intent preference"
            android:summary="Launches an Activity from an Intent">
            <intent
                android:action="android.intent.action.VIEW"
                android:data="http://www.baidu.com"/>
        </PreferenceScreen>

    </PreferenceCategory>
    <PreferenceCategory
        android:key="prf_key_att"
        android:title="preference attributes">
        <CheckBoxPreference
            android:key="prf_key_ck_parent"
            android:title="parent checkbox preference"
            android:summary="This is visually a parent">

        </CheckBoxPreference>
        <CheckBoxPreference
            android:key="prf_key_ck_child"
            android:title="Child Checkbox preference"
            android:summary="This is visually a child"
            android:dependency="prf_key_ck_parent">

        </CheckBoxPreference>
    </PreferenceCategory>
</PreferenceScreen>
```
MainActivity.java
```
package com.example.win.systemsetup;

import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
       // setContentView(R.layout.activity_main);

        getFragmentManager().beginTransaction()
                .replace(android.R.id.content, new SettingsFragment())
                .commit();

    }
}
```
