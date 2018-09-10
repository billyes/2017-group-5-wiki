# Design
<!-- TOC -->

- [Design](#design)
    - [Team Information](#team-information)
    - [Vision Statement](#vision-statement)
    - [Feature List](#feature-list)
        - [Domain Analysis](#domain-analysis)
        - [Create a profile](#create-a-profile)
        - [Request Access](#request-access)
        - [Tutorial](#tutorial)
        - [Evaluate Image Quality](#evaluate-image-quality)
        - [Analyzing an Item](#analyzing-an-item)
        - [Geolocation](#geolocation)
        - [Handling Unrecognized Objects → relevance feedback → training clarifai](#handling-unrecognized-objects-→-relevance-feedback-→-training-clarifai)
        - [Feedback for Incorrectly Categorized Items](#feedback-for-incorrectly-categorized-items)
        - [User Experience](#user-experience)
        - [Hardware](#hardware)
    - [UI Sketches](#ui-sketches)
    - [Prototypes](#prototypes)
    - [Use Cases](#use-cases)
        - [User creates a profile](#user-creates-a-profile)
        - [User starts an app](#user-starts-an-app)
        - [User takes a photo for evaluation/analysis](#user-takes-a-photo-for-evaluationanalysis)
        - [Allows user to locate trash can](#allows-user-to-locate-trash-can)
        - [Allows user to add unrecognized trash can](#allows-user-to-add-unrecognized-trash-can)
        - [Allows user to provide feedback](#allows-user-to-provide-feedback)
        - [Allow User to view History Graph](#allow-user-to-view-history-graph)
        - [Allow Gamification](#allow-gamification)
    - [Endpoints](#endpoints)
    - [UML Diagram](#uml-diagram)
    - [Architecture](#architecture)
        - [Client Side](#client-side)
        - [Server Side](#server-side)
        - [Libraries](#libraries)
        - [FrontEnd](#frontend)
        - [BackEnd](#backend)
        - [Framework](#framework)
        - [DB](#db)
    - [Initial Code](#initial-code)

<!-- /TOC -->
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
- (Extended) Compress image and store for the user to review later.

### Analyzing an Item
- Allow user to take a picture of their item.
- (Extended) Analyze a live stream instead of pictures.
- Identify an object in an image and tell you what type of trash it is.
    - Recyclable, Compost, or Trash
    - (Extended) TerraCycling, Plastic Bags, clothes, etc

### Geolocation
- Tells you locations of nearby trash bins.
- Allow user to manually enter the GPS coordinates of new trash bins.
- (Extended) Allow user to add a picture of the trashcan to the trash can’s location.
- (Extended) Allow up vote and down vote of bins in case they moved.
- Determine where the closest disposal unit is.
- (Extended) Give user directions to nearest location.
- If there are 2 trashcans within a certain threshold of proximity, indicate that there are 2 trashcans in the area.
- (Extended) If the user selects to get directions to one of the trashcans, randomly decide which trashcan to send them to and which picture to display.

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
- Add a graphical representation indicating the percentage of images documented that were trash, recycle, and compost.
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

## Prototypes

![](https://github.com/jhu-oose/2017-group-5/blob/master/Iteration2/prototype1.jpg)

![](https://github.com/jhu-oose/2017-group-5/blob/master/Iteration2/prototype2.jpg)

## Use Cases

### User creates a profile 
1. User opens app for the first time.
1. User has options to sign in with Facebook or sign up natively. 
    1. If sign up natively, User need to fill out following information: 
        1. Username, first name, last name, password, email (optional)
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

### Allow User to view History Graph
1. User selects to view History Graph.
1. Calculate percent of history that was trash, compost, and recycle. This can be done by accessing the integer variable that stores the amount of photos of a trash, compost, or recycle and dividing that by the total number of items logged.
1. Display percentages to user.

### Allow Gamification
1. User selects to implement Gamification
1. User can select to link to Facebook
1. User logs into Facebook
1. (Extended) User can add friends based on Facebook friends list
1. When user takes a picture, record the object in our database
1. Search user’s history to see how frequently the user’s disposes an object of this type. If it is infrequent, allocate a large point value.
1. Search overall user history to see how frequently all user’s dispose of an object of this type. If it is infrequent, allocate a large point value.
1. Determine point value of item based on user’s history.  and rarity of item.
1. Increase user’s point total based on history.
1. Allow user to view a top 10 list for friend’s points
1. Give list of rewards for different point values. Possible prizes include new skins for app, cover photo access, etc.

## Endpoints

| Description                      | Method | URL                    | Content                                                    | Success Response                                            | Failure Response                                     |
| :------------------------------: | :----: | :--------------------: | :--------------------------------------------------------- | :---------------------------------------------------------- | :--------------------------------------------------- |
| **USER**                         |
| Create a new user                | POST   | /v1/users              | { id, username, password, firstname, lastname, timestamp } | 200, Content: {}                                            | 401, Content: { Reason: "Invalid User Information" } |
| Update user information          | PUT    | /v1/users/{id}         | {}                                                         | 200, Content: {}                                            | 401, Content: { Reason: "Invalid User ID" }          |
| Delete user                      | DELETE | /v1/users/{id}         | {}                                                         | 200, Content: {}                                            | 401, Content: { Reason: "Invalid User ID"}           |
| Get user information             | GET    | /v1/users/{id}         | {}                                                         | 200, Content: { user }                                      | 401, Content: { Reason: "Invalid User ID" }          |
| Get user history                 | GET    | /v1/users/{id}/history | {}                                                         | 200, Content: { history }                                   | 401, Content: { Reason: "Invalid User ID" }          |
| Get top rankers                  | GET    | /v1/rankings           | {}                                                         | 200, Content: { topUsers }                                  | 404, Content: {}                                     |
| **IMAGE TRANACTION**             |
| Process and evaluate image       | POST   | /v1/images             | { id, image, timestamp }                                   | 200, Content: {}                                            | 405, Content: {}                                     |
| Send user feedback               | POST   | /v1/feedback           | { id, feedback }                                           | 200, Content: {}                                            | 406, Content: {}                                     |
| **UTILITIES**                    |
| Add a new trashcan               | POST   | /v1/api/trashcans      | { id, lat, lon, added_by, timestamp }                      | 200, Content: {}                                            | 407, Content: {}                                     |
| Upvote or downvote a trashcan    | PUT    | /v1/api/trashcans/{id} | { id, action }                                             | 200, Content: {}                                            | 408, Content: {}                                     |
| Get trashcan coordinates         | GET    | /v1/api/trashcans      | { trashcans }                                              | 200, Content: {}                                            | 409, Content: {}                                     |
| Get trashcan information         | GET    | /v1/api/trashcans/{id} | {}                                                         | 200, Content: { id, date_added, lat, lon, comments, votes } | 409, Content: {}                                     |
| Get a single history information | GET    | /v1/api/histories/{id} | {}                                                         | 200, { id, timestamp, lat, lon, type }                      | 409, Content: { }                                    |



## UML Diagram

![Jiwon's UML Diagram Link in the parantheses ->](https://github.com/jhu-oose/2017-group-5/blob/master/Iteration2/UML.png)

## Architecture

![](https://github.com/jhu-oose/2017-group-5/blob/master/Iteration2/Architecture.png)

### Client Side 

- By using React Native, we will create the front end to send requests to the web server and receive responses/results from the server. (follow up on end-points section for more details) 

### Server Side
 
- By using Python Django, we will use MTV model to communicate web server. 
- The main job of backend will be to communicate with Clarifai API and process with the results to get an accurate classification of recyclable, or compost. 
- For training purpose, we will be training the model of Clarifai with pre-collected dataset and will improve the accuracy by retrieving feedbacks from user (which are to be stored in S3 with corresponding images) and re-training with it. 
- Back-end will also deal with storing and retrieving data from PostgreSQL by using Models. 
We are debating between AWS or Heroku for deployment method, but since we will user S3 for storing images, we will end up with AWS.


### Libraries 
- Clarifai (https://www.clarifai.com/)
- S3 
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
	


## Initial Code
- We have implemented much of the front-end. This includes a dummy log-in screen, camera, and results page after taking a photo. In the back end, we have tested Clarifai by writing short scripts on connected to Clarifai with image file and retreive results. This code is presented in "clarify_prototype.py" script.
- We have also collected a database of pictures that we can use for testing throughout the project. As we move forward, we will integrate more pictures we have taken ourselves. Images are in PhotoSet folder.
