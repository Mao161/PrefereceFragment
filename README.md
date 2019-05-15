# 实验四 扩展的Activity




## 添加 PreferenceFragment 
~~~
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        // Display the fragment as the main content.
        getFragmentManager().beginTransaction()
                .replace(android.R.id.content, new SettingsFragment())
                .commit();
    }
    public static class SettingsFragment extends PreferenceFragment {
        @Override
        public void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);

            // Load the preferences from an XML resource
            addPreferencesFromResource(R.xml.preferences);
        }
    }
    
    
~~~



## 1.In-line preferences
###    CheckBoxPreference
### 关键代码：
~~~
    <PreferenceCategory
        android:title="In-line preferences"
        android:key="pref_key_Inline"
        >
        <CheckBoxPreference
            android:key="pre_CheckBox1"
            android:title="Checkbox preference"
            android:summary="This is a checkbox"
            android:defaultValue="true"
           />
    </PreferenceCategory>
~~~



 ## 2.Dialog-based preferences
###   EditTextPreference
###   ListPreference
###  关键代码：
~~~
 <PreferenceCategory
        android:title="Dialog-based preferences"
        android:key="pref_key_Dialogbased"
        >
        <EditTextPreference
            android:key="pre_key_EditText1"
            android:title="Edit text preference"
            android:summary="An Example that uses an edit text dialog"
            />
        <ListPreference
            android:key="myList_Preference"
            android:title="List preference"
            android:summary="An example that uses a list dialog"
            android:entries="@array/theArry"
            android:entryValues="@array/theArry"
            android:dialogTitle="Chooese one"
            />
    </PreferenceCategory>
~~~




## Launch preferences
###  PreferenceScreen: 跳转到另一个PreferenceScreen
###  PreferenceScreen: 启动一个网页
###  关键代码：
~~~
 <PreferenceCategory
        android:title="Launch preferences"
        android:key="pref_key_Launch"
        >
        <PreferenceScreen
            android:key="pref_key_screen"
            android:title="Screen preference"
            android:summary="Shows another screen of preferences"
            >
            <CheckBoxPreference
                android:key="pre_CheckBox2"
                android:title="Checkbox preference"
                android:summary="This is a checkbox"
                android:defaultValue="true"
                />
        </PreferenceScreen>
        <Preference
            android:title="Intent preference"
            android:summary="Luaches an Activity from an Intent"
            >
            <intent
                android:action="android.intent.action.VIEW"
                android:data="http://www.baidu.com/"
                />
        </Preference>
    </PreferenceCategory>
~~~



## Preference attributes
### CheckBox: 父选项
### CheckBox: 子选项，当父选项勾选时呈现
###  关键代码：

~~~
    <PreferenceCategory
        android:title="Preference attributes"
        android:key="PreferenceCategory_key">

        <CheckBoxPreference
            android:key="pre_CheckBox3"
            android:summary="This is visually a parent"
            android:title="Parent checkboxs preference"
            android:defaultValue="false" />

        <CheckBoxPreference
            android:key="pre_CheckBox4"
            android:summary="This is visually a child"
            android:title="Child chechbox preference"
            android:dependency="pre_CheckBox3"
            android:defaultValue="false"/>

    </PreferenceCategory>
~~~
 ### 结果截图：
![](http://ww1.sinaimg.cn/large/005LTKwJgy1g32f7utdjgj30930g80u1.jpg)

![](http://ww1.sinaimg.cn/large/005LTKwJgy1g32f8kabtoj30930g875h.jpg)

![](http://ww1.sinaimg.cn/large/005LTKwJgy1g32f8qrz1bj30930g875h.jpg)

![](http://ww1.sinaimg.cn/large/005LTKwJgy1g32f8wobyzj30930g8q3k.jpg)

![](http://ww1.sinaimg.cn/large/005LTKwJgy1g32f96dpbbj30930g8myd.jpg)

![](http://ww1.sinaimg.cn/large/005LTKwJgy1g32f9c2ma3j30930g875m.jpg)



