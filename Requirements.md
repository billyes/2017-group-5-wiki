# Team Not Trash
- [Iteration 1](#iteration-1)
    - [Team Information](#team-information)
    - [Vision Statement](#vision-statement)
    - [Feature List](#feature-list)
        - [Create a profile](#create-a-profile)
        - [Request Access](#request-access)
        - [Tutorial](#tutorial)
        - [Evaluate Image Quality](#evaluate-image-quality)
        - [Analyzing an Item](#analyzing-an-item)
        - [Geolocation](#geolocation)
        - [Handling Unrecognized Objects → relevance feedback → training clarifai](#handling-unrecognized-objects-%E2%86%92-relevance-feedback-%E2%86%92-training-clarifai)
        - [Feedback for Incorrectly Categorized Items](#feedback-for-incorrectly-categorized-items)
        - [User Experience](#user-experience)
        - [Hardware](#hardware)
    - [UI Sketches](#ui-sketches)
    - [Use Cases](#use-cases)
        - [User creates a profile](#user-creates-a-profile)
        - [User starts an app](#user-starts-an-app)
        - [User takes a photo for evaluation/analysis](#user-takes-a-photo-for-evaluationanalysis)
        - [Allows user to locate trash can](#allows-user-to-locate-trash-can)
        - [Allows user to add unrecognized trash can](#allows-user-to-add-unrecognized-trash-can)
        - [Allows user to provide feedback](#allows-user-to-provide-feedback)
        - [Allow Gamification (Extended)](#allow-gamification-extended)
    - [Architecture](#architecture)
        - [Libraries](#libraries)
        - [FrontEnd](#frontend)
        - [BackEnd](#backend)
        - [Framework](#framework)
        - [DB](#db)

# Iteration 1

## Team Information

Service Name: Not Trash

Group Number 5

Members: Baekchun Kim, Jiwon Shin, Hailey Lee, Sung Woo Park, Sienna Schmid

## Vision Statement

We have found that people have problems knowing whether something is compostable, recyclable, or just trash. Oftentimes, people simply throw everything into incinerate bin even though their trash is recyclable. We want to make this easier for them so less items go into our incinerators and landfills.
We are creating an app for our users that will analyze their trash on the go. Our app will let the user take a picture of an item they want to dispose and tell them which category it falls into. The goal is to encourage the users to use alternatives to a trashcan and to decrease contamination from non-compostable and non-recyclables being put into the bins.

## Feature List

### Domain Analysis

![](https://github.com/jhu-oose/2017-group-5/blob/master/Iteration1/domain.png)


### Create a profile
- Prompt user to create account through Facebook, Google or natively within the app.
- If created natively:
- Collect first name.
- Collect last name.
- Collect password.
- Collect email address.
- Edit profile elements.

### Request Access
- Prompt user to allow access the device’s camera.
- Prompt user to allow access the device’s geographical location.

### Tutorial
- For the first time user, provide brief guideline of how to use the app.

### Evaluate Image Quality
- Take a photo of the item.
- If the image be of low quality(unrecognizable), prompt the user to enter the type of object. 
- (Extended) Before retaking the picture, show a clear photo of an item that was recognizable by our app as an example to the user.

### Analyzing an Item
- Allow user to take a picture of their item.
- (Extended) Analyze a live stream instead of pictures.
- Identify an object in an image and tell you what type of trash it is.
    - Recyclable, Compost, or Trash
    - (Extended) TerraCycling, Plastic Bags, clothes, etc

### Geolocation
- Tells you locations of nearby trash bins.
- Allow user to manually enter the GPS coordinates of new trash bins.
- (Extended) Allow up vote and down vote of bins in case they moved.
- Determine where the closest disposal unit is.
- (Extended) Give user directions to nearest location.

### Handling Unrecognized Objects → relevance feedback → training clarifai
- If an object cannot be recognized or categorized, prompt user to enter information.
- Allow user to input what the object is and how it should be sorted.

### Feedback for Incorrectly Categorized Items
- Allow user to provide feedback on the result if it is inaccurate or can be improved. 

### User Experience
- Allow the user to leave the camera to view their profile.
- (Extended) Implement point system among users at Hopkins. (Gamification)
- (Extended) View their earned points.
- List user’s history of activities such as which item was recycled, composed at which date. 
- (Extended) Add a graphical representation of the usage list.
- (Extended) Suggest life improvements such as use of reusable water bottle.
- (Extended) Add nearby friends through Facebook.
- (Extended) Add events from the Office of Sustainability. 

### Hardware
- (Extended) Create a Trashcan that will auto-sort the trash to the right bin.


## UI Sketches
![](https://github.com/jhu-oose/2017-group-5/blob/master/Iteration1/screen1.png)

![](https://github.com/jhu-oose/2017-group-5/blob/master/Iteration1/screen2.png)

![](https://github.com/jhu-oose/2017-group-5/blob/master/Iteration1/screen3.png)

![](https://github.com/jhu-oose/2017-group-5/blob/master/Iteration1/screen4.png)

![](https://github.com/jhu-oose/2017-group-5/blob/master/Iteration1/screen5.png)

![](https://github.com/jhu-oose/2017-group-5/blob/master/Iteration1/screen6.png)

![](https://github.com/jhu-oose/2017-group-5/blob/master/Iteration1/screen7.png)

![](https://github.com/jhu-oose/2017-group-5/blob/master/Iteration1/screen8.png)


## Use Cases

### User creates a profile 
1. User opens app for the first time.
1. User has options to sign in with Facebook, Google, or sign up natively. 
    1. If sign up natively, User need to fill out following information: 
        1. ID, first name, last name, password, email (optional)
1. User signs up and creates an account successfully
1. User logs into account and app opens the camera as the first page.

### User starts an app 
1. (First time only) User has to authorize camera access and location access for extended features. 
1. (First time only) User will be prompted to finish optional tutorial
1. Once app has an access to the camera, user will see camera screen as the first screen. 
1. User can take photo of an object for further steps. 

### User takes a photo for evaluation/analysis 
1. The user opens to a camera for quick access
1. The user takes a picture of an item.
1. The app prompts for “Take another photo” if the photo is of low quality and is not able to analyze. 
1. The app returns whether it is recyclable, compost or trash.

### Allows user to locate trash can
1. The app asks if user wants directions to the nearest bin.
1. User enters the map screen.
1. The app shows all bins near by the user. 
1. User chooses the nearest bin they want to be directed to. 
1. The app gives directions to the chosen bin. 

### Allows user to add unrecognized trash can
1. User enters the map screen. 
1. User chooses ‘add trash can’. 
1. User locates the trash can. 
1. The app allows user to up vote or down vote the trash can (To check whether the located trash can is not accurate information)

### Allows user to provide feedback 
1. After returning the result of recyclable, compost, or trash, the app prompts : “ Is this correct? Please tell us !” 
1. User chooses to give feedback. 
1. User enters comments ( e.g. correct object )

### Allow Gamification (Extended)
1. User selects to implement Gamification
1. User can select to link to Facebook
1. User logs into Facebook
1. User can add friends based on Facebook friends list
1. When user takes a picture, record the object in our database
1. Increase user’s point total based on rare-ness of item
    1. (how to determine this)

## Architecture

![](https://github.com/jhu-oose/2017-group-5/blob/master/Iteration1/architecture.png)

### Libraries 
- Clarifai (https://www.clarifai.com/)
- Facebook Login 
- Google Login

### FrontEnd 
- React Native (for iOS)
	
### BackEnd 
- Python
	
### Framework 
- Django
	
### DB 
- PostgreSQL
	
