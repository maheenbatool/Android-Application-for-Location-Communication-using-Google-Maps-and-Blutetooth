# Android-Application-for-Location-Communication-using-Google-Maps-and-Blutetooth-Module

I used Android studio for designing android application, as it is the official IDE
for android applications development. Before starting making any android application,
to make a virtual device which can be developed by launching Android AVD
Manager in the Android Studio after its installation. After the completion of android
application code, its compilation generates an archive file with extension “.apk”, which
contains all the contents of the android application necessary for installation of application. 
Gradle File
Android studio keeps things nice and less complicated by providing all the necessary
tools and features in one place. Things get complicated when we need to interact with
other elements. Gradle is actually build automation tool, which means it helps the android studio to compile all the other files in one APK file. Normally, gradle does it work itself. we don’t have to put extra effort, only if sometimes advanced features are needed to be added then we have to jump into it. There are normally two Gradle files, one for the complete project and one for the application.

Manifest File
In this file all the components of android application are declared. It is necessary to
define all the components on manifest file. Manifest file is also responsible for the
user permissions that an application requires, for example in our application we needs
permission to turn on the Bluetooth and location. It also declares the API level which
is needed by the application. It declares the hardware and software features, such as
camera, Bluetooth etc. we needed an API library for the Google map, which is also the
Arduino Based Train Collision Warning System
responsibility of manifest file.

Java File
The java code and its functionality can be divided into five steps as shown below;

1 Turn on the Bluetooth
For the first step of turning on the Bluetooth we made a function called Oncreat() function, it checks if the Bluetooth is on or not. If the Bluetooth is on it will call the function
Searchdevices(), and if it is not on it will start an intent to take the permission from user
to turn on the Bluetooth. Intent is an object that provides the binding during runtime
between components, components could be any two activities. Intents can be used for
many tasks, in our case it started to take the permission for turning on the Bluetooth.
mBluetoothAdapter.cancelDiscovery();
Log.d(TAG,”DiscoveryCanceled.”);
int MY_PerREQAcc_Co_Loc = 1;
ActCom.requestPermission(this,newString[]Manifest.permission.AC
Ces_Co_Loc,
MY_Per_Req_Acc_Co_Loc);
mBluetoothAdapter.startDiscovery();
65
ANDROID APPLICATION
Log.d(TAG,”Discovery Started.”);

2 Search Bluetooth Devices
This function gets the permission of turning on the location which is necessary for the
Bluetooth. Then it will start the discovery to search for the Bluetooth devices, if any
device is found it will add it to the list and will keep searching for more devices.

3 Connect to Selected Device
From the list of found Bluetooth devices, when we select a particular device to pair the
function OnItemClick() is called. This function tries to create a bond with the selected
Bluetooth device. After the successful connection, it calls the function Map().
if (mBTDevices.get(i).getBondState() == BOND\_BONDED && opened==1){Map();}}
public void onFinish()
{if (mBTDevices.get(i).getBondState() == BOND_NONE) { }}

4 Display Map
When the function Map() is being called after the successful pairing of Bluetooth device, layout of the application changes to Google map. So this Map() function basically
changes the layout of the application. Map() function initializes the button for view settings and calls the map fragment and getLatLong() function.
Private GoogleMap mMap;
Marker marker1, marker2;
LatLng latlngModule1, latlngModule2;
Button b1,b2,b3;
int choice = 1;
TextView textview2, textview4, textview5, textview6, textview7;
String slat1,slong1,slat2,slong2, sdistance;
66
Arduino Based Train Collision Warning System
It applies the haversine formula on the received data from getLetLong() function. On
this map activity, the calculated distance is also displayed. Two markers are also added
for the position of trains.

5 Display Data from the Bluetooth
GetLatLong() function gets the data from the Bluetooth devices, separates position parameters of both the modules and throw back the data to Map() function. This functions
applies firstly differentiate between the position parameters of both the modules, then
applies the conditions opposite to that applied on the Bluetooth module data in Arduino
code.
byte[] buffer = new byte[1024];
int bytes;
try {
bytes = inputStream.read(buffer);
ByteArrayInputStream input = new ByteArrayInputStream(buffer);
recieved = new String(buffer);
String[] values = recieved.split("\n");
slat1 = values[0];
slat2 = values[1];
slong1 = values[2];
slong2 = values[3];
if (slat1 != null && slat2!= null && slong1!= null && slong2!= null) {
Lat1 = Double.parseDouble(slat1)/1000000;
Lat2 = Double.parseDouble(slat2)/1000000;
if (Lat2 < 0) {
Lat2 = Lat2 + 180;}
if (Lat2 >= 0) {
Lat2 = Lat2 - 180;}
Long1 = Double.parseDouble(slong1)/1000000;
67
ANDROID APPLICATION
if (Long1 < 0) {
Long1 = Long1 + 360;}
if (Long1 >= 0) {
Long1 = Long1 - 360;}
Long2 = Double.parseDouble(slong2)/1000000;
if (Long2 < 0) {
Long2 = Long2 + 550;}
if (Long2 >= 0) {
Long2 = Long2 - 550;
}}
if (slat1 == null && slat2== null && slong1== null && slong2== null)
{Log.d ("String", "IS EMPTY");
}Log.d("String", "Written");
} catch (IOException e) {
e.printStackTrace();
}}}

XML File
The layout of android applications is handled a piece of code, whose file is called activity_main.xml. XML is a markup language which basically defines the layout of the android application. It is not really a programming, we setup our layout and the code
is generated, so basically it is a code file. For example, if we want to put a button in
our android application we will place it in the layout using activity_main.xml, and what
happens what this button is pressed is put in the java code. In our android application
we have three XML files as shown below;
