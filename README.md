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
___________________________________

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



________________________
# USER INTERACTIONS
__________________________
__________________________

### Toast Message
______________________

It can be used to display information for short period of time. A toast contains message to be displayed quickly and disappears after sometime.

<img width="365" alt="Screenshot 2023-12-11 at 3 52 03 AM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/3bb4ad6e-fb1f-425c-b4c2-acd5335d0ccb">
<img width="343" alt="Screenshot 2023-12-11 at 3 52 19 AM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/feaefae1-5949-467a-a475-bb30a9ee4001">

```
package com.xyz.toast_kotlin

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button
import android.widget.Toast

class MainActivity : AppCompatActivity() {

    lateinit var buttonToast : Button

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        buttonToast = findViewById(R.id.buttonToast)

        buttonToast.setOnClickListener {
            Toast.makeText(applicationContext, "This is a Toast Message", Toast.LENGTH_LONG).show()
        }
    }
}
```

### SnackBar Message
___________________________

It is a light-weight widget and it is used to show messages in the bottom of the application with swiping enabled.

<img width="349" alt="Screenshot 2023-12-11 at 4 15 52 AM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/092012b8-4c2e-44c7-8aaa-b6f49c3e0372">
<img width="339" alt="Screenshot 2023-12-11 at 4 16 01 AM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/03612995-2cdf-4ea6-b194-82b3b806e03a">

```
package com.xyz.toast_kotlin

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.view.View
import android.widget.Button
import android.widget.Toast
import androidx.constraintlayout.widget.ConstraintLayout
import com.google.android.material.snackbar.Snackbar

class MainActivity : AppCompatActivity() {

    lateinit var buttonToast : Button
    lateinit var buttonSnackbar : Button
    lateinit var myLayout : ConstraintLayout

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        buttonToast = findViewById(R.id.buttonToast)
        buttonSnackbar = findViewById(R.id.buttonSnackbar)
        myLayout = findViewById(R.id.mylayout)

        buttonToast.setOnClickListener {
            Toast.makeText(applicationContext, "This is a Toast Message", Toast.LENGTH_LONG).show()
        }

        buttonSnackbar.setOnClickListener {
            Snackbar.make(myLayout, "This is a snackbar message", Snackbar.LENGTH_INDEFINITE).setAction("Close", View.OnClickListener {  }).show()
        }
    }
}
```

### Dialog Message
__________________________

A dialog is a small window that prompts the user to make a decision or enter additional information. A dialog does not fill the screen and is normally used for modal events that require users to take an action before they proceed.


<img width="355" alt="Screenshot 2023-12-21 at 8 39 44 AM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/41270302-d254-4fd1-b901-79d7b6e74009">

<img width="359" alt="Screenshot 2023-12-21 at 8 39 53 AM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/f0642068-82b2-474b-9dc8-41a69c6086f5">
<img width="359" alt="Screenshot 2023-12-21 at 8 40 03 AM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/d4fa3d8f-8410-4210-88ed-26fb41454674">


```
package com.xyz.toast_kotlin

import android.content.DialogInterface
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.view.View
import android.widget.Button
import android.widget.Toast
import androidx.appcompat.app.AlertDialog
import androidx.constraintlayout.widget.ConstraintLayout
import com.google.android.material.snackbar.Snackbar

class MainActivity : AppCompatActivity() {

    lateinit var buttonToast : Button
    lateinit var buttonSnackbar : Button
    lateinit var myLayout : ConstraintLayout
    lateinit var showDialogMessage : Button

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        buttonToast = findViewById(R.id.buttonToast)
        buttonSnackbar = findViewById(R.id.buttonSnackbar)
        myLayout = findViewById(R.id.mylayout)
        showDialogMessage = findViewById(R.id.buttonDialogMessage)

        buttonToast.setOnClickListener {
            Toast.makeText(applicationContext, "This is a Toast Message", Toast.LENGTH_LONG).show()
        }

        buttonSnackbar.setOnClickListener {
            Snackbar.make(myLayout, "This is a snackbar message", Snackbar.LENGTH_INDEFINITE).setAction("Close", View.OnClickListener {  }).show()
        }

        showDialogMessage.setOnClickListener {
            showAlertDialog()
        }

    }

    fun showAlertDialog()
    {
        var alertDialog = AlertDialog.Builder(this@MainActivity)

        alertDialog.setTitle("Change")
            .setMessage("Do you want to change the text of the button?")
            .setIcon(R.drawable.alert)
            .setCancelable(false)
            .setNegativeButton("No", DialogInterface.OnClickListener { dialog, which ->

                dialog.cancel()

            })

            .setPositiveButton("Yes", DialogInterface.OnClickListener { dialog, which ->

                showDialogMessage.text = "Alert Dialog"
            })

        alertDialog.create().show()

    }
}
```

# List And Views
___________________

### ListView
_______________

List view is a view which groups several items and display them in vertical scrollable list.

<img width="346" alt="Screenshot 2024-01-01 at 10 56 13 AM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/af842118-4297-47b7-9ced-472e7fa4fc67">
<img width="342" alt="Screenshot 2024-01-01 at 10 56 43 AM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/0d638f77-94f0-4103-aea9-768adf2e4f05">

MainActivity.kt
```
package com.xyz.listview_kotlin

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.ArrayAdapter
import android.widget.ListView
import android.widget.Toast

class MainActivity : AppCompatActivity() {

    lateinit var listView: ListView

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        listView = findViewById(R.id.listcountry)

        var country = resources.getStringArray(R.array.Countries)

        var arrayAdapter = ArrayAdapter(this, android.R.layout.simple_list_item_1, country)

        listView.adapter = arrayAdapter

        listView.setOnItemClickListener { parent, view, position, id ->
            val countryName: String = listView.getItemAtPosition(position).toString()

            Toast.makeText(applicationContext, "You selected the country  " +countryName, Toast.LENGTH_LONG).show()
        }
        

    }
}
```

Strings.xml
```
<resources>
    <string name="app_name">ListView_KOTLIN</string>
    
    <string-array name="Countries">
        <item>America</item>
        <item>Austria</item>
        <item>Australia</item>
        <item>Armenia</item>
        <item>Alaska</item>
        <item>Antarctica</item>
        <item>Belgium</item>
        <item>Brooklyn</item>
        <item>Canada</item>
        <item>Cuba</item>
        <item>Denmark</item>
        <item>Egypt</item>
        <item>France</item>
        <item>Germany</item>
        <item>Hungary</item>
        <item>Iceland</item>
        <item>India</item>
        <item>Jericho</item>
        <item>Jakarta</item>
        <item>Krygystan</item>
        <item>London</item>
        <item>Mexico</item>
        <item>Miami</item>
        <item>Netherlands</item>
        <item>Norway</item>
        <item>Oslo</item>
        <item>Peru</item>
        <item>Quebec</item>
    </string-array>
</resources>
```

### Recycler View
___________________

It is more advanced version of ListView with improved performance and other benefits. It can take position horizontally and vertically.

<img width="343" alt="Screenshot 2024-01-01 at 11 07 09 AM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/2df11edb-2d62-4204-ac86-abcb63ecceee">
<img width="343" alt="Screenshot 2024-01-01 at 11 07 41 AM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/0db5d1b5-219f-40b1-95c0-40e794a7a1fd">

MainActivity.kt
```
package com.xyz.recyclerview_kotlin

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import androidx.recyclerview.widget.LinearLayoutManager
import androidx.recyclerview.widget.RecyclerView

class MainActivity : AppCompatActivity() {

    lateinit var recylerView: RecyclerView

    var contactNameList = ArrayList<String>()
    var numberList = ArrayList<String>()
    var imageList = ArrayList<Int>()

    lateinit var adapter: contactAdapter

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        recylerView = findViewById(R.id.recylerView)

        recylerView.layoutManager = LinearLayoutManager(this@MainActivity)

        contactNameList.add("Didi")
        contactNameList.add("Mutesh")
        contactNameList.add("Nono")

        numberList.add("+91 9483362342")
        numberList.add("+91 9462863729")
        numberList.add("+91 7791823546")

        imageList.add(R.drawable.didi)
        imageList.add(R.drawable.mutesh)
        imageList.add(R.drawable.nono)

        adapter = contactAdapter(contactNameList, numberList, imageList, this@MainActivity)

        recylerView.adapter = adapter

    }
}
```

contactAdapter.kt
```
package com.xyz.recyclerview_kotlin

import android.content.Context
import android.view.LayoutInflater
import android.view.View
import android.view.ViewGroup
import android.widget.TextView
import android.widget.Toast
import androidx.cardview.widget.CardView
import androidx.recyclerview.widget.RecyclerView
import de.hdodenhof.circleimageview.CircleImageView

class contactAdapter(
    var contactNameList: ArrayList<String>,
    var numberList: ArrayList<String>,
    var imageList: ArrayList<Int>,
    var context: Context) : RecyclerView.Adapter<contactAdapter.ContactViewHolder>(){

    class ContactViewHolder(itemView: View) : RecyclerView.ViewHolder(itemView){
        var textViewName : TextView = itemView.findViewById(R.id.textViewName)
        var textViewNumber : TextView = itemView.findViewById(R.id.textViewNumber)
        var ImageView : CircleImageView = itemView.findViewById(R.id.imageView)
        var cardView : CardView = itemView.findViewById(R.id.cardView)
    }

    override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): ContactViewHolder {

        val view : View = LayoutInflater.from(parent.context)
            .inflate(R.layout.card_design, parent, false)

        return ContactViewHolder(view)
    }

    override fun getItemCount(): Int {
        return contactNameList.size
    }

    override fun onBindViewHolder(holder: ContactViewHolder, position: Int) {

        holder.textViewName.text = contactNameList.get(position)
        holder.textViewNumber.text = numberList.get(position)
        holder.ImageView.setImageResource(imageList.get(position))

        holder.cardView.setOnClickListener {
            Toast.makeText(context, "You selected the contact of " + contactNameList.get(position), Toast.LENGTH_LONG ).show()
        }
    }

}
```

### GridView
________________

It shows items in two dimensional scrolling grid (rows and coloumns) and the grid items are not necessarily predetrmined but they automatically get inserted to the layout using a list adapter.

<img width="346" alt="Screenshot 2024-01-01 at 4 54 38 PM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/2657503d-b5e1-4d24-8dfa-b7d1b38fa8e3">
<img width="339" alt="Screenshot 2024-01-01 at 4 54 44 PM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/4677f9b6-b275-4a4e-a948-94a221fdc8a4">


MainActivity.kt

```
package com.xyz.gridview_kotlin

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Adapter
import android.widget.GridView
import android.widget.Toast

class MainActivity : AppCompatActivity() {

    lateinit var gridView: GridView
    var nameList = ArrayList<String>()
    var imageList = ArrayList<Int>()

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        gridView = findViewById(R.id.gridView)
        fillArrays()

        val adapter = AnimalAdapter(this,nameList, imageList)
        gridView.adapter = adapter

        gridView.setOnItemClickListener { adapterView, view, position, id ->
            Toast.makeText(applicationContext, "You selected the ${nameList[position]} animal", Toast.LENGTH_LONG).show()
        }

    }

    fun fillArrays(){
        nameList.add("sparrow")
        nameList.add("Monkey")
        nameList.add("Dog")
        nameList.add("Cat")
        nameList.add("Cow")
        nameList.add("Horse")
        nameList.add("Rabbit")
        nameList.add("Donkey")
        nameList.add("Snake")

        imageList.add(R.drawable.sparrow)
        imageList.add(R.drawable.monkey)
        imageList.add(R.drawable.dog)
        imageList.add(R.drawable.cat)
        imageList.add(R.drawable.cow)
        imageList.add(R.drawable.horse)
        imageList.add(R.drawable.rabbit)
        imageList.add(R.drawable.donkey)
        imageList.add(R.drawable.snake)

    }
}
```

AnimalAdapter.kt

```
package com.xyz.gridview_kotlin

import android.content.Context
import android.view.LayoutInflater
import android.view.View
import android.view.ViewGroup
import android.widget.BaseAdapter
import android.widget.ImageView
import android.widget.TextView

class AnimalAdapter(
    var context: Context,
    var nameList: ArrayList<String>,
    var imageList: ArrayList<Int>
) : BaseAdapter() {


    override fun getCount(): Int {
        return nameList.size
    }

    override fun getItem(position: Int): Any? {
        return null
    }

    override fun getItemId(position: Int): Long {
        return 0
    }

    override fun getView(position: Int, convertView: View?, parent: ViewGroup?): View {
        val view : View = LayoutInflater.from(parent!!.context)
            .inflate(R.layout.custom_layout,parent,false)

        val animalName : TextView = view.findViewById(R.id.textView)
        val animalImage : ImageView = view.findViewById(R.id.imageView)

        animalName.text = nameList[position]
        animalImage.setImageResource(imageList.get(position))

        return view
    }

}
```

### ScrollView

When an app has a layout that has a content that might be longer then the height of the device and that content must be vertically scrollable then we use scroll view.


### WebView

It is an android component which allows to display content from the web directly inside an application.

```
package com.xyz.scrollview_kotlin

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.webkit.WebView
import android.webkit.WebViewClient
import androidx.activity.OnBackPressedCallback

class MainActivity : AppCompatActivity() {

    lateinit var webView: WebView

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        webView = findViewById(R.id.web)

        webView.webViewClient = WebViewClient()
        webView.loadUrl("https://github.com/0XKCD0/Android_notes/edit/main/README.md")

        onBackPressedDispatcher.addCallback(this, callback)
    }

    val callback = object : OnBackPressedCallback(true){
        override fun handleOnBackPressed() {
            if (webView.canGoBack()){
                webView.goBack()
            }
            else{
                finish()
            }
        }

    }

}
```

# Intent and LifeCycle
_________________________

### Intent
_______________

An intent is an object that provides runtime binding between seperate components, such as two activities.
The intent represents an app's intent to do something.

<img width="314" alt="Screenshot 2024-01-02 at 3 22 31 PM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/82e70dca-da6b-4468-b09f-84cd2c24d2e4">
<img width="307" alt="Screenshot 2024-01-02 at 3 22 37 PM" src="https://github.com/0XKCD0/Android_notes/assets/123825075/2b247756-514f-4803-b78c-3530a5fe521b">

MainActivity.kt
```
package com.xyz.intent

import android.content.Intent
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button
import android.widget.EditText

class MainActivity : AppCompatActivity() {

    lateinit var name: EditText
    lateinit var age : EditText
    lateinit var sendButton : Button

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        name = findViewById(R.id.editTextName)
        age = findViewById(R.id.editTextNumber)
        sendButton = findViewById(R.id.send)


        sendButton.setOnClickListener {

            var userName = name.text.toString()
            var userAge = age.text.toString().toInt()

            var intent = Intent(this@MainActivity, SecondActivity::class.java)

            intent.putExtra("username", userName)
            intent.putExtra("userage", userAge)


            startActivity(intent)

        }
    }
}
```

SecondActivity.kt

```
package com.xyz.intent

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.TextView

class SecondActivity : AppCompatActivity() {
    lateinit var text : TextView
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_second)

        text = findViewById(R.id.textView)

        var userName : String = intent.getStringExtra("username").toString()
        var userAge : Int = intent.getIntExtra("userage", 0)

        text.text = "The username is $userName and his/her age is $userAge"

    }
}
```

### Application Lifecycle
_____________________________

![Android-Activity-Lifecycle](https://github.com/0XKCD0/Android_notes/assets/123825075/ea81e3ea-2aa9-43b1-8db3-636636677597)


### Fragment Lifecycle
___________________________


### Services
___________________

A service is an application component that can perform long-running operations in the background. Services do not provide a user-interface.
+ Foreground service
+ Background service
+ Bound service

Services has two classes:
+ 


# Shared Preferences And Data Saving

_______________________________________

### Shared Preferences
________________________

It allows you to save and retrieve data in the form of value pair and key.
It allows you to save and retrieve primitive data types (Interger, float, Boolean, String, Long) data.
The shared preference file is managed by an android framework and it can be accessed anywhere within the app to read or write the data into the file.

# Architectural Room Database
_______________________________

### Room Database
__________________

A new concept for creating database in Android applications. Introduced Google Room Database at Google IO 2017.
Room database creates an Abstract layer above the SQLite Database.

Room database has 3 components:
+ Entity - sets/hold field values
+ Database Access Objects - Get entities from database. Persist changes again back to database.
+ Database

Room database transactions
+ Create database
+ Create table
+ Add new Data (Insert)
+ Show data in app (Query)
+ Data update (Update)
+ Data delete (Delete)









































