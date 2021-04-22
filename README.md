# Market_Place
A Social Platform to Buy and Sell Stuff

## Table of Contents
1. [Overview](#Overview)
1. [Product Spec](#Product-Spec)
1. [Wireframes](#Wireframes)

## Overview
### Description
Basically allows users to connect to new people and Buy/ Sell stuff. User can also report corrupt posts/users, review their experience or could just post pictures.  
Could be potentially as a common platform to connect with new people as well as buy/sell stuff.

### App Evaluation
- **Category:** Social Networking / Digital Market
- **Mobile:** This app would be primarily developed for Ios devices.
- **Story:** Analyzes users location , and connects them to nearby users and available posts to Buy and also allow USer to put up stuff to sell. The user can then decide to message this person/ post if wanted.
- **Market:** Any individual could choose to use this app, and to keep it a safe environment, people would be organized into age groups.
- **Habit:** This app could be used as often or unoften as the user wanted depending on their needs and social life, and what exactly they're looking for.
- **Scope:** First we would start with suggesting people/ posts based on location and user preference, then perhaps this could evolve into a sharing application to broaden its usage. Large potential for use with ability to view and review posts from eBay, Facebook, or digital selling/buying applications.

## Product Spec
### 1. User Stories (Required and Optional)

**Completed User Stories**
* Not yet completed.

**Required Must-have Stories**

* User logs in to access previous posts and change preference settings
* User can search for particular category of items.]
* User can connect woth other people.
* User can also provide feedback, report inappropriate Users. They also have a chat window to get to know each other.
* Profile pages for each user
* Settings (Accesibility, Notification, General, etc.)

**Optional Nice-to-have Stories**

* Log of past posts/people with farther location.
* Page of most viewed posts 

### 2. Screen Archetypes

* Login 
* Register - User signs up or logs into their account
   * Upon Download/Reopening of the application, the user is prompted to log in to gain access to their profile information to be properly matched with another person. 
* Messaging Screen - Chat for users to communicate (direct 1-on-1)
   * Upon selecting a particular user post, it will go to message screen.
* Profile Screen 
   * Allows user to upload a photo and fill in information that is interesting to them and others
* Posts Screen 
   * Allows user to upload a photo of the item and fill in information and the cost
* Settings Screen
   * Lets people change language, and app notification settings.

### 3. Navigation

**Tab Navigation** (Tab to Screen)

* Category selection
* Profile
* Settings

Optional:
* Discover (Top Choices)

**Flow Navigation** (Screen to Screen)
* Forced Log-in -> Account creation if no log in is available
* Post Selection  -> Jumps to Chat
* Profile -> Text field to be modified. 
* Settings -> Toggle settings

## Wireframes
<img src="https://github.com/IOSAppProject-MarketPlace/Market_Place/blob/main/CamScanner%2004-08-2021%2019.07.jpg" width=800><br>


## Schema
### Models
#### Post
|Property      |Type         |Description                                     |
|--------------|-------------|------------------------------------------------|
|userId        |String       |unique id for the user post (default field)     |
|author        |Pointer      |to User	image author                          |
|image	       |File         |image that user posts                           |
|caption       |String       |image caption by author                         |
|Amount        |Alpha-Numeric|amount for a product                            |
|likesCount    |Number       |number of likes for the post                    |
|createdAt     |DateTime     |date when post is created (default field)       |
|updatedAt     |DateTime     |date when post is last updated (default field)  |

## Networking
### List of network requests by screen
- Home Feed Screen
  (Read/GET) Query all posts where user is user
```
let query = PFQuery(className:"Post")
query.whereKey("user", equalTo: currentUser)
query.order(byDescending: "createdAt")
query.findObjectsInBackground { (posts: [PFObject]?, error: Error?) in
   if let error = error { 
      print(error.localizedDescription)
   } else if let posts = posts {
      print("Successfully retrieved \(posts.count) posts.")
  // TODO: Do something with posts...
   }
}
```
- (Create/POST) Create a new like on a post
- (Delete) Delete existing like
- (Create/POST) Create a new comment on a post
- (Delete) Delete existing comment
- Create Post Screen
  (Create/POST) Create a new post object
- Profile Screen
  (Read/GET) Query logged in user object
  (Update/PUT) Update item image

