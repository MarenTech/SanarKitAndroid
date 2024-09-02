# SanarKit - Android

SanarKit - is a Android SDK designed to seamlessly integrate Sanar services into your iOS application. It simplifies the process of connecting to Sanar's services, managing user sessions, and handling the complete booking and post-booking flows, including appointment and provider communication.

## Download the Latest Release of SanarKit

To get started with integrating the SanarKit Android library into your application, you first need to download the latest release of the library from the official repository. Follow the steps below:

- Visit the GitHub Releases Page:
Go to the SanarKit releases page by clicking on the following link: [SanarKit Android Library Releases](https://github.com/MarenTech/KotlinSanarKit/releases/).

- Download the Latest Release:
    - On the releases page, locate the latest release version at the top of the list.
    - Click on the release version to expand the details, and then download the .zip file.
    - Extract the zip file then you will get the .aar file associated with that release.

### The SanarKit will support the following Implementations:

- ## [connect](#connect-1)
- ## [disconnect](#disconnect-1)
- ## [gotoBookingView](#gotobookingview-1)
- ## [gotoAppointmentListView](#gotoappointmentlistview-1)

### Initializing and Using the SanarKit Android SDK

## Initialization

```kotlin
val sanarKit = SanarKit(this)
```

`this`: Represents the application context. You should pass the context of your Android application to the `SanarKit` constructor.

### SanarKit implementations
# Connect 
The SanarKit SDK provides a seamless way to integrate authentication and connection services into your Android applications. One of the key methods in the SDK is connect, which allows your application to authenticate with SanarServices. To effectively integrate authentication and connection services into your iOS application using the SanarKit SDK, you should ensure the following:

    - Initialization: Before invoking any Sanar flows or making use of other SDK features, you must initialize the SDK. This typically involves setting up required configurations and ensuring that your application is properly set up to communicate with SanarServices.

    - Calling `connect`: The `connect` method should be called as an essential step to authenticate with SanarServices. This method establishes a connection and handles authentication, which is crucial for accessing any subsequent SDK functionalities or services.

```kotlin
sanarKit.connect(
   authToken = "<client-id>",
   userInfo = userInfo,
   bundleId = "com.example.demo"
)
```

Parameters : 

`authToken` (String) : The authentication token provided by the service. Replace "<client-id>" with your actual client ID or token.

`bundleId` (String) : The bundleId parameter represents the unique bundle identifier for your Android application. It ensures that the request is coming from the correct application and is used to validate the app with the Sanar Services.

`lang` (String) Optional :  the language parameter to switch between Arabic and English, default value will be English. To change the language pass the lang parameter in the connect method.

Change Language Example : 

```kotlin
sanarKit.connect(
    authToken = "<client-id>",
    userInfo = userInfo,
    bundleId = "com.example.demo",
    lang = "ar" // en
)
```

`userInfo` ([UserInfo](#userinfo-)) : An instance of the UserInfo class that contains the user or client data that needs to be sent to the SanarService to create the User Session

The UserInfo object must be initialized with the following fields:

```kotlin
val userInfo = UserInfo(
    firstName = "<first_name>",
    lastName = "<last_name>",
    dob = "<yyyy-mm-dd>",
    gender = "M",
    nationality = "<nationality>",
    documentId = "2469433220",
    mid = "MG2",
    documentType = 1,
    phoneCode = "<phone_code>",
    phoneNo = "<phone_number>",
    maritalStatus = "0"
)
```

### userInfo : 
Property | Description
:--- | :---
first_name : string | User first name
last_name : string  | User last name
dob : string  | dob in `yyyy-mm-dd`
gender : string  | Gender `M` | `F`
nationality : string | Nationality of User ex : Saudi Arabia.
document_id : string | Document id Default `1`
mid : string | Member id 
document_type: number | Document Type
phone_code : string  | Phone code ex : `966`
phone_no : string | Phone Number
marital_status : string | Marital status `0` : `Unmarried`, `1` : `Married`

### Example Usage : 
Here is a complete example of how to initialize the SanarKit SDK and connect to the service:

```kotlin
val sanarKit = SanarKit(this)

val userInfo = UserInfo(
    firstName = "John",
    lastName = "Doe",
    dob = "1994-08-13",
    gender = "M",
    nationality = "Saudi Arabia",
    documentId = "2469433220",
    mid = "MG2",
    documentType = 1,
    phoneCode = "91",
    phoneNo = "81794771111",
    maritalStatus = "0"
)

sanarKit.connect(
    authToken = "<client-id>",
    userInfo = userInfo,
    bundleId = "com.example.demo"
)
```

# disconnect
The SanarKit SDK also provides a method to disconnect from the SanarKit service, which is useful for terminating an existing connection when it's no longer needed.

### Usage
To disconnect from the SanarKit service, simply call the disconnect method on your SanarKit instance:

```kotlin
sanarKit.disconnect()
```

Best Practices: It's good practice to call disconnect when your app is about to be suspended, or when the user logs out or navigates away from sections of the app that require a connection to the SanarKit service.

# gotoBookingView
The SanarKit SDK provides a convenient method called `gotoBookingView` that allows your application to navigate directly to the Sanar Booking flow. This method handles the complete booking process within the SDK, simplifying the integration and eliminating the need for extensive additional development, including the creation of UI interfaces.

To navigate to the Sanar Booking flow, simply call the `gotoBookingView` method on your SanarKit instance:

```kotlin
sanarKit.gotoBookingView()
```

### Description : 

- Booking Flow Integration: The gotoBookingView method takes care of navigating to and managing the entire booking process within the SanarKit SDK. This includes displaying the booking UI, managing user interactions, and handling all backend communications required to complete a booking.

- No Additional UI Required: By using gotoBookingView, you can integrate the booking functionality without needing to design or implement any additional UI components. The SDK provides a ready-to-use interface that blends seamlessly with your application.


# gotoAppointmentListView
he SanarKit SDK provides a method called `gotoAppointmentListView` that allows your application to navigate directly to the post-booking flow. This flow includes functionalities such as viewing appointment lists, accessing appointment details, and chatting with the provider. By utilizing `gotoAppointmentListView`, your app can seamlessly manage the post-booking process within the SDK, reducing the need for additional development and providing a smooth user experience.

To navigate to the post-booking flow, simply call the `gotoAppointmentListView` method on your `SanarKit` instance:

```kotlin
sanarKit.gotoAppointmentListView()
```

### Description : 

- Post-Booking Management: The gotoAppointmentListView method allows your application to access and manage all post-booking activities within the SanarKit SDK. This includes:
    - Viewing Appointment Lists: Users can see a list of all their upcoming and past appointments.
    - Accessing Appointment Details: Users can view detailed information about each appointment, such as time, date, and service provider details.
    - Chatting with Providers: Users can initiate and continue conversations with their service providers directly from the appointment details view.

- No Additional UI Required: Similar to other methods in the SanarKit SDK, gotoAppointmentListView comes with a fully integrated user interface. This eliminates the need for developing custom UI components, making it easier and faster to implement post-booking features in your app.

For more details and implementation examples, please check the example repository [Here](https://github.com/MarenTech/ExampleSanarKitAndroid).


