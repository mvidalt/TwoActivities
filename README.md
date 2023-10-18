# TwoActivities
## 2.2: Activity Lifecycle and Instance State 
In this practical you'll learn more about the activity lifecycle. The activity lifecycle is the set of states an activity can be in  during its entire lifetime, from the time it is initially created to when it is destroyed and the system reclaims that activity's  resources. As a user navigates between activities in your app (as well as into and out of your app), those activities each  transition between different states in the activity lifecycle. 

Each stage in the lifecycle of an activity has a corresponding callback method (onCreate(), onStart(), onPause(), and so on). When an activity changes state, the associated callback method is invoked. You've already seen one of these methods:  onCreate(). By overriding any of the lifecycle callback methods in your activity classes, you can change the default behavior of how your activity behaves in response to different user or system actions. 

Changes to the activity state can also occur in response to device configuration changes such as rotating the device from  portrait to landscape. These configuration changes result in the activity being destroyed and entirely recreated in its default  state, which may cause the loss of information the user has entered in that activity. It's important to develop your app to  prevent this to avoid user confusion. Later in this practical we'll experiment with configuration changes and learn how to  preserve the state of your activities in response to device configuration changes or other Activity lifecycle events. 

In this practical you'll add logging statements to an app and observe the lifecycle changes as you use the app in various  ways. You will then begin working with these changes and exploring how to handle user input under these conditions. 
## App Overview 
For this practical you'll need to create a new app.  
## Task 1. Add Lifecycle Callbacks to TwoActivities 
In this task you will implement all of the activity lifecycle callback methods to print messages to logcat when those methods are invoked. These log messages will allow you to see when the activity lifecycle changes state, and how those lifecycle state  changes affect your app as it runs. 
### 1.1 Implement callbacks in to MainActivity 
#### 1. Open MainActivity. 

#### 2. In the onCreate() method, add the following log statements: 
```Log.d(LOG_TAG, "-------"); 
Log.d(LOG_TAG, "onCreate");
```


#### 3. Add a new method for the onStart() callback, with a statement to the log for that event: 
```
@Override 
public void onStart(){  
super.onStart();  
Log.d(LOG_TAG, "onStart"); 
} 
```

TIP: Select Code > Override Methods in Android Studio. A dialog appears with all of the  possible methods you can override in your class. Choosing one or more callback methods from  the list inserts a complete template for those methods, including the required call to the  superclass. 
#### 4. Use the onStart() method as a template to implement the other lifecycle callbacks: 

• onPause()
  	
• onRestart()  
	
• onResume()  

• onStop()  

• onDestroy() 



#### 5. Build and run your app. 

### 1.2 Implement lifecycle callbacks in SecondActivity 
Now that you've implemented the lifecycle callback methods for MainActivity, create a second Activity and do the  same for SecondActivity. 

#### 1. Open java/com.example.android.twoactivities/SecondActivity. 


#### 2. At the top of the class, add a constant for the LOG_TAG variable: 
```private static final String LOG_TAG = SecondActivity.class.getSimpleName(); 	```
#### 3. Add the lifecycle callbacks and log statements to the second activity. (You can also just copy and paste the  callback methods from MainActivity) 

#### 4. Add a log statement to the returnReply() method, just before the finish() method: 
```Log.d(LOG_TAG, "End SecondActivity");```


#### 5. Insert a button to the first Activity to call the second one. Hint: 
```
Intent intent = new Intent(this,SecondActivity.class); 
startActivityForResult(intent); 
```







1.3 Observe the log as the app runs 
1. Run your app. 
2. Click Android Monitor at the bottom of Android Studio to open the Android Monitor. 
3. Select the logcat tab. 
4. Type "Activity" in the Android Monitor search box. 
The Android logcat can be very long and cluttered. Because the LOG_TAG variable in each class contains either the  words MainActivity or SecondActivity, this keyword lets you filter the log for only the things you're interested in. 





Experiment using your app and note that the lifecycle events occur in response to  
different actions. In particular, try these things: 
* Use the app normally (send a message, reply with another message.) 
* Use the back button to go back from the second activity to the main activity. 
* Use the left arrow in the action bar to go back from the second activity to the main activity. • Rotate the device on both the main and second activity at different times in your app and observe what  happens in the log and on the screen. TIP: If you're running your app in an emulator, you can simulate  rotation with Ctrl-F11 or Ctrl-Fn-F11. 
* Press the overview button (the square button to the right of Home) and close the app (tap the X).  • Return to the home screen and restart your app. 

Challenge: Watch for onDestroy() in particular. Why is onDestroy() called sometimes (after clicking the back  button, or on device rotation) and not others (manually stopping and restarting the app)? 
Hint: https://developer.android.com/guide/components/activities/activity-lifecycle
