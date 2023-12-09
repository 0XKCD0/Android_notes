# Android_notes
Important notes on Android studio with Kotlin


### What is android studio?
________________________________

Android is a software package and linux based operating system for mobile devices such as tablet computers and smartphones.
It is developed by Google and later the OHA (Open Handset Alliance). 

### OHA
_________________
It's a consortium of 84 companies such as google, samsung, AKM, synaptics, KDDI, Garmin, Teleca, Ebay, Intel etc.

### Features of Android
_____________________________

1) It is open-source.

2) Anyone can customize the Android Platform.

3) There are a lot of mobile applications that can be chosen by the consumer.

4) It provides many interesting features like weather details, opening screen, live RSS (Really Simple Syndication) feeds etc.

5) It provides support for messaging services(SMS and MMS), web browser, storage (SQLite), connectivity (GSM, CDMA, Blue Tooth, Wi-Fi etc.), media, handset layout etc.

### Android Architecture
___________________________________

Android architecture or Android software stack is categorized into five parts:

+ linux kernel
+ native libraries (middleware),
+ Android Runtime
+ Application Framework
+ Applications

  **Android Architecture**

  ![softwarestack](https://github.com/0XKCD0/Android_notes/assets/123825075/4257f78b-45bc-4856-9026-a851609f9101)

### APK file
___________________

An apk file is created by the framework automatically. If you want to run the android application on the mobile, transfer and install it.

### Manifest file
_____________________

Every project in Android includes a Manifest XML file, which is AndroidManifest.xml, located in the root directory of its project hierarchy. The manifest file is an important part of our app because it defines the structure and metadata of our application, its components, and its requirements. This file includes nodes for each of the Activities, Services, Content Providers, and Broadcast Receivers that make the application, and using Intent Filters and Permissions determines how they coordinate with each other and other applications.

### res/values File
______________________

The res/values folder is used to store the values for the resources that are used in many Android projects to include features of color, styles, dimensions etc.
+ colors.xml
+ strings.xml
+ styles.xml
+ dimens.xml

### Gradle file
___________________

Gradle is a build system (open source) that is used to automate building, testing, deployment, etc. “build.gradle” are scripts where one can automate the tasks.
Every Android project needs a Gradle for generating an apk from the .java and .xml files in the project.

1) Top-level build.gradle - It is located in the root project directory and its main function is to define the build configurations that will be applied to all the modules in the project. It supports :
   + buildscripts
   + dependencies
2) Module-level build.gradle - Located in the project/module directory of the project this Gradle script is where all the dependencies are defined and where the SDK versions are declared. This script has many functions in the project which include additional build types and override settings in the main/app manifest or top-level build.gradle file. It supports:

+ android: This block is used for configuring the specific android build options. 
   - compileSdkVersion – This is used to define the API level of the app and the app can use the features of this and lower level. 
+ defaultConfig: 
   - applicationId– This is used for identifying unique id for publishing of the app.
   - minSdkVersion– This defines the minimum API level required to run the application.
   - targetSdkVersion– This defines the API level used to test the app.
   - versionCode– This defines the version code of the app. Every time an update needs to be of the app, the version code needs to be increased by 1 or more.
   - versionName– This defines the version name for the app. this could be increased by much while creating an update.
+ buildTypes(release): 
   - minifyEnabled– this will enable code shrinking for release build.
   - proguardFiles– this will specify the progaurd settings file.
+ dependencies: This specifies the dependencies that are needed to build the project.


# Android Components
_________________________________

### Layouts
______________
It is an interface that we use to place android components in android application. Basically, a layout defines the visual structure for user interface. We use layouts to put components in a particular order.
+ Linear
+ Relative
+ Table
+ Constraint - It is the main layout. It gives flexible and adaptable ways to create views for the app. It allows us to create complex and dynamic and responsive views in a flat hierarchy.

### TextViews
_______________________

It is a user interface element that displays text to user. It is used as a label or print some result on the screen or print some notification. 

<img width="441" alt="Screenshot 2023-12-03 at 10 21 03 PM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/c1d79fcf-4b5c-4a86-aa75-1ed8e13792d1">     
<img width="441" alt="Screenshot 2023-12-03 at 10 21 13 PM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/112ad2db-bb15-40e4-a628-b28c64f05b0d">

```
package com.xyz.examplekotlin

import android.graphics.Color
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.TextView


class MainActivity : AppCompatActivity() {

    lateinit var myText: TextView

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        myText = findViewById(R.id.textexample)
        myText.setTextColor(Color.BLUE)
        myText.setText("This is just an example to be checked")
        myText.setOnClickListener {
            myText.setTextColor(Color.GREEN)
            myText.setBackgroundColor(Color.GRAY )

        }
    }
}
```

### Buttons
________________________

Buttons represents a push button. Buttons can be pressed by the user to perform some actions.

<img width="378" alt="Screenshot 2023-12-03 at 11 11 30 PM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/51178754-57bf-4621-ac5e-671fc21668fd">
<img width="358" alt="Screenshot 2023-12-03 at 11 11 48 PM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/ae7161a8-1bce-425c-a021-0f7f8f2d2dc4">
<img width="363" alt="Screenshot 2023-12-03 at 11 12 08 PM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/1ea3107e-d8c9-4817-983a-0ef8dc6241c1">

```
package com.xyz.buttonkotlin

import android.graphics.Color
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button
import android.widget.TextView
import androidx.core.view.isVisible

class MainActivity : AppCompatActivity() {

    lateinit var domagic: Button
    lateinit var clickmagic: Button
    lateinit var myText: TextView

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        domagic = findViewById(R.id.do_magic)
        clickmagic =findViewById(R.id.click_magic)
        myText= findViewById(R.id.textView)

        clickmagic.setOnClickListener {
            myText.setText("Magic is this. Cringe Magic!!!")
            myText.setTextColor(Color.BLACK)
            myText.setBackgroundColor(Color.LTGRAY)
            domagic.isVisible = false
        }

        domagic.setOnClickListener {
            myText.setText("I know this is a not a very good application. But I'm on it.")
            myText.setTextColor(Color.YELLOW)
            myText.setBackgroundColor(Color.GREEN)
            clickmagic.isVisible = false
        }
    }

}
```
### EditText
_________________

Edit texts are user interface component in Android studio that allows user to enter or modify texts.

<img width="365" alt="Screenshot 2023-12-07 at 12 24 49 AM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/2f2b01e1-694a-4d00-96ea-76ba148d8d7d">
<img width="358" alt="Screenshot 2023-12-07 at 12 25 00 AM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/e7b674b6-1389-447e-b331-189d98a485e4">


### ImageView
____________________________


It is used to display an image file in android application.


<img width="368" alt="Screenshot 2023-12-07 at 1 10 41 AM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/165512b3-0420-4894-b102-3ddd564baaec">
<img width="349" alt="Screenshot 2023-12-07 at 1 10 50 AM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/03a06e4d-fe68-44c4-a137-2bfe4bcc66e1">

```
package com.xyz.edittext_kotlin

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button
import android.widget.EditText
import android.widget.ImageView
import android.widget.TextView

class MainActivity : AppCompatActivity() {

    lateinit var name: EditText
    lateinit var ok: Button
    lateinit var result: TextView
    lateinit var image: ImageView

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        name = findViewById(R.id.editTextTextperson)
        ok = findViewById(R.id.button1)
        result = findViewById(R.id.textView2)
        image = findViewById(R.id.fuck_image)

        ok.setOnClickListener {
            var userName: String = name.text.toString()
            result.setText(userName)
            image.setImageResource(R.drawable.tom)
        }
    }
}
```

### CheckBox
___________________

It is a type of two state button either unchecked or checked.


<img width="364" alt="Screenshot 2023-12-07 at 7 16 13 PM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/a2405453-fb81-4a52-881d-192537ae47f5">
<img width="366" alt="Screenshot 2023-12-07 at 7 16 27 PM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/e56693b4-f9fe-4544-a0be-e144036712e6">
<img width="353" alt="Screenshot 2023-12-07 at 7 16 38 PM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/b79ad941-de4f-4bdc-8965-9f0ed7655324">

```
package com.xyz.checkboxes_kotlin

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.CheckBox
import android.widget.TextView

class MainActivity : AppCompatActivity() {

    lateinit var male: CheckBox
    lateinit var female: CheckBox
    lateinit var result: TextView

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        male = findViewById(R.id.check_male)
        female = findViewById(R.id.check_female)
        result = findViewById(R.id.textView)

        male.setOnClickListener {
            if (male.isChecked){
                result.text = "Your gender is male"
                female.isChecked = false
            }
            else{
                result.text = "What is your gender?"
            }
        }

        female.setOnClickListener {
            if (female.isChecked){
                result.text = "Your gender is female."
                male.isChecked = false
            }
            else{
                result.text = "What is your gender?"
            }
        }
    }
}
```

### RadioButton
_____________________

It allows the user to select one option from the set. We use radio Buttons for optional sets that are mutually exclusive if you think that the user wants to see all available options side by side.

<img width="364" alt="Screenshot 2023-12-07 at 8 07 24 PM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/92a22070-b9d7-41fa-9ab9-133db8e2f2b4">
<img width="376" alt="Screenshot 2023-12-07 at 8 07 36 PM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/50d03883-3423-4b8d-a8e2-da7cffea22fd">
<img width="355" alt="Screenshot 2023-12-07 at 8 07 49 PM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/6ceef0d7-86ac-4b15-b0f3-bdbd64618cfc">
<img width="359" alt="Screenshot 2023-12-07 at 8 08 01 PM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/74daaf54-d64e-49f5-91d2-310b1c48b994">

```
package com.xyz.radiobutton_kotlin

import android.graphics.Color
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button
import android.widget.LinearLayout
import android.widget.RadioButton

class MainActivity : AppCompatActivity() {

    lateinit var LinearLayout : LinearLayout
    lateinit var Green: RadioButton
    lateinit var Yellow : RadioButton
    lateinit var Red : RadioButton
    lateinit var Change : Button

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        Green = findViewById(R.id.RadioButtonGreen)
        Yellow = findViewById(R.id.RadioButtonYellow)
        Red = findViewById(R.id.RadioButtonRed)
        Change = findViewById(R.id.button_change)
        LinearLayout = findViewById(R.id.linear_layout)

        Change.setOnClickListener {
            if (Green.isChecked){
                LinearLayout.setBackgroundColor(Color.GREEN)
            }
            else if (Yellow.isChecked){
                LinearLayout.setBackgroundColor(Color.YELLOW)
            }
            else if (Red.isChecked){
                LinearLayout.setBackgroundColor(Color.RED)
            }
        }
    }
}
```

### Toggle Buttons
_________________________

Allows user to change a setting between two states.

<img width="365" alt="Screenshot 2023-12-09 at 8 07 36 AM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/f99fd6b5-79df-4764-917a-ff70ca262f0e">
<img width="361" alt="Screenshot 2023-12-09 at 8 07 48 AM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/e9c1ecc6-1977-4a03-bf58-91885935e427">

```
package com.xyz.toggle_button_kotlin

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.view.View
import android.widget.ImageView
import android.widget.TextView
import android.widget.ToggleButton

class MainActivity : AppCompatActivity() {

    lateinit var image: ImageView
    lateinit var result: TextView
    lateinit var button: ToggleButton

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        image = findViewById(R.id.tom)
        result = findViewById(R.id.text1)
        button = findViewById(R.id.toggleButton)

        button.setOnCheckedChangeListener { buttonView, isChecked ->

            if (isChecked){
                image.visibility = View.INVISIBLE
                result.text = "The image is invisible"
            }
            else{
                image.visibility = View.VISIBLE
                result.text = "The image is visible now"
            }
        }
    }
}
```

### Spinner
____________________

Spinner is a view similar to the dropdown list which is used to select one option from the list of options. It provides an easy way to select one item from the list of items and it shows a dropdown list of all values when we click on it.

<img width="345" alt="Screenshot 2023-12-09 at 10 17 57 AM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/9040e052-ef1e-4539-ad75-80bd9fa1f1f4">
<img width="351" alt="Screenshot 2023-12-09 at 10 18 08 AM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/d1742279-1ac5-49c1-813e-7b3757aef64b">

strings.xml file
```
<resources>
    <string name="app_name">Spinner-Kotlin</string>
    <string-array name="countries">
        <item>India</item>
        <item>Sri Lanka</item>
        <item>Bangladesh</item>
        <item>Nepal</item>
        <item>Pakistan</item>
        <item>China</item>
        <item>Japan</item>
        <item>America</item>
        <item>Australia</item>
        <item>South Korea</item>
        <item>England</item>
        <item>Canada</item>
        <item>South Africa</item>
    </string-array>
</resources>
```

MainActivity.kt file
```
package com.xyz.spinner_kotlin

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.view.View
import android.widget.AdapterView
import android.widget.ArrayAdapter
import android.widget.Spinner
import android.widget.TextView

class MainActivity : AppCompatActivity(), AdapterView.OnItemSelectedListener {

    lateinit var result: TextView
    lateinit var spinner: Spinner

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        result = findViewById(R.id.textView)
        spinner = findViewById(R.id.spinner)

        spinner.onItemSelectedListener = this

        var arrayAdapter = ArrayAdapter.createFromResource(
            this, R.array.countries, android.R.layout.simple_spinner_item
        )

        arrayAdapter.setDropDownViewResource(android.R.layout.simple_spinner_item)
        spinner.adapter = arrayAdapter
    }

    override fun onItemSelected(parent: AdapterView<*>?, view: View?, position: Int, id: Long) {
        if (parent != null){
            result.text = parent.getItemAtPosition(position).toString()
        }
    }

    override fun onNothingSelected(parent: AdapterView<*>?) {

    }
}
```

### Top App Bar
______________________

It provides content and action to the current screen. It is also known as action bar. It is used for branding, screen titles, navigation and actions.


























