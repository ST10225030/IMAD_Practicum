# IMAD_Practicum
Comprehensive Report  

The first page in my application is the splash screen. This class is responsible for displaying a splash screen with two buttons: one to enter the main activity and another to exit the application. There are two buttons, "buttonEnter" and "buttonExit," are defined in the layout file. Click listeners are set for these buttons to handle user interactions. The SplashActivity class in Kotlin handles the initialization of the splash screen layout and defines the behavior for the "Enter" and "Exit" buttons. When the "Enter" button is clicked, it starts the MainActivity and finishes the current activity. Clicking the "Exit" button simply finishes the activity, effectively closing the application. This page links to the main activity page. 

 

A screenshot of a cell phone

Description automatically generated 

The next page is the MainActivity code snippet showcases the setup of the main activity in an Android application. It initializes the UI, handles button click events, and navigates to the HomeActivity upon button click.  This page navigates to the home activity page when the button is clicked. 

A screenshot of a weather app

Description automatically generated 

 

The Third page of my application is the Home page. The app consists of two activities -HomeActivity and DetailedViewActivity. The HomeActivity is the main activity where users can enter and save their screen time data. The DetailedViewActivity displays the saved screen time data in a detailed view. The layout of the HomeActivity is defined in the activity_home.xml file. It includes EditText fields for date, morning screen time, afternoon screen time, and notes. It also includes buttons for saving, clearing, and navigating to the detailed view. The screen time data is stored in an ArrayList of ScreenTimeEntry objects. Each ScreenTimeEntry object represents a single entry with the date, morning screen time, afternoon screen time, and notes. There are three buttons on this page, the save button saves the user input on the application. The clear button clears out all the typed information that the user enters if they made a mistake and wants to clear the information out. The next button prompts the user to the next page where all their recorded data is stored.  

A screenshot of a weather conditioner

Description automatically generated 

The last page in my application is the detailed activity view page. This activity displays detailed information about screen time entries, calculates averages, and populates a ListView with the detailed information. The code retrieves a list of ScreenTimeEntry objects from the intent extras. It initializes and finds UI elements like ListView, TextView, and Button. It calculates the average morning and afternoon screen times based on the data. It populates the ListView with detailed information about each screen time entry. It finishes the activity when the back button is clicked. 

 

PSEUDOCODE 

Splash screen: 

1. Start 
2. Create a package named com.example.imadprecticum 
3. Import necessary libraries: android.content.Intent, androidx.appcompat.app.AppCompatActivity,  
   android.os.Bundle, android.widget.Button 
4. Define a class SplashActivity which extends AppCompatActivity 
5. Create an override function onCreate with a parameter savedInstanceState of type Bundle 
6. Call the superclass method onCreate with the savedInstanceState parameter 
7. Set the content view to R.layout.activity_splash 
8. Find the "Enter" button in the layout and set a click listener 
9. Inside the click listener for the "Enter" button: 
    9.1. Start the MainActivity by creating an intent and passing it to startActivity 
    9.2. Finish the SplashActivity 
10. Find the "Exit" button in the layout and set a click listener 
11. Inside the click listener for the "Exit" button: 
    11.1. Finish the SplashActivity 
12. End 

Main Activity: 

1. Start 
2. Create a package named com.example.imadprecticum 
3. Import necessary libraries: android.annotation.SuppressLint, android.content.Intent,  
   androidx.appcompat.app.AppCompatActivity, android.os.Bundle, android.widget.Button,  
   androidx.activity.enableEdgeToEdge 
4. Define a class MainActivity which extends AppCompatActivity 
5. Create an override function onCreate with a parameter savedInstanceState of type Bundle 
6. Call the superclass method onCreate with the savedInstanceState parameter 
7. Enable edge-to-edge display on supported devices 
8. Set the content view to R.layout.activity_main 
9. Find the "Home" button in the layout and assign it to a variable named button 
10. Set a click listener on the button 
11. Inside the click listener: 
    11.1. Create an Intent to start the HomeActivity 
    11.2. Start the HomeActivity using the intent 
12. End 

Home Activity: 

1.Start  

2.Define a package named com.example.imadprecticum 

3.Import necessary classes and modules 

  

4.Define a class named HomeActivity which inherits from AppCompatActivity 

5.Declare private variables to store user input 

6.Initialize an ArrayList to store ScreenTimeEntry objects 

7.Define onCreate method with savedInstanceState parameter 

8.Call superclass onCreate method passing savedInstanceState 

9.Set content view to activity_home layout 

10.Initialize EditText variables to reference corresponding views in the layout 

11.Initialize Button variables to reference corresponding views in the layout 

12.Set click listeners for buttons 

13.When save button is clicked, call saveData method 

14.When clear button is clicked, call clearData method 

15.When next button is clicked 

16.Create an Intent to switch to DetailedViewActivity 

17.Put screenTimeData ArrayList as an extra in the Intent 

18.Start DetailedViewActivity using the Intent 

19.Define saveData method 

20.Get text from EditText fields 

21.Check if any field is empty 

22.If yes, display a toast message and return 

23.Create a new ScreenTimeEntry object with user input data 

24. Add the entry to screenTimeData ArrayList 

25.Display a toast message indicating successful data saving 

26.Define clearData method 

27. Clear text from all EditText fields 

28.Display a toast message indicating successful data clearing 

29.End 

 

Detailed View Activity: 

1.BEGIN DetailedViewActivity 

   2. FUNCTION onCreate(savedInstanceState: Bundle) 

        3.CALL super.onCreate(savedInstanceState) 

       4. CALL setContentView(R.layout.activity_detailed_view2) 

  

        5.// Retrieve data from intent 

        6.data = CALL intent.getParcelableArrayListExtra<ScreenTimeEntry>("data") 

        7.IF data IS NULL THEN 

            8.data = Empty ArrayList 

        9.END IF 

  

        // Initialize views 

        10.listView = CALL findViewById<ListView>(R.id.listView) 

        11.averageTextView = CALL findViewById<TextView>(R.id.average_info) 

        12.btnBack = CALL findViewById<Button>(R.id.buttonBack) 

  

        // Calculate total morning and afternoon times 

        13.totalMorning = 0.0 

        14.totalAfternoon = 0.0 

        15.FOR EACH entry IN data DO 

            16.totalMorning = totalMorning + entry.morning 

            17.totalAfternoon = totalAfternoon + entry.afternoon 

        18.END FOR 

  

        // Calculate averages 

        19.IF data.isNotEmpty() THEN 

            20.averageMorning = totalMorning / data.size 

            21.averageAfternoon = totalAfternoon / data.size 

        ELSE 

            22.averageMorning = 0.0 

            23.averageAfternoon = 0.0 

        24.END IF 

  

        // Display average times 

        25.CALL averageTextView.setText("Average Morning: " + averageMorning + 26."\nAverage Afternoon: " + averageAfternoon) 

  

        // Populate ListView with detailed information 

        27.detailedInfoList = Empty List 

        28.FOR EACH entry IN data DO 

            29.detailedInfoList.add("Date: " + entry.date + "\nMorning: " + entry.morning + 30."\nAfternoon: " + entry.afternoon + "\nNotes: " + entry.notes) 

        31.END FOR 

  

        // Set adapter for ListView 

        32.adapter = CALL ArrayAdapter(this, android.R.layout.simple_list_item_1, detailedInfoList) 

        33.CALL listView.setAdapter(adapter) 

  

        // Set click listener for the "Back" button to finish the activity 

        34.CALL btnBack.setOnClickListener { 

            35.CALL finish() 

        } 

    36.END FUNCTION 

37.END DetailedViewActivity 

References: 

Logo Creator - Make a logo with Free Logo Design 

IMAD5112 Practicum Guide 2024 
