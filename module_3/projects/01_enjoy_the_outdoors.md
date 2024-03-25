# Capstone Project: Enjoy the Outdoors
In this project, you will build an application that helps a user find things to do to enjoy the great outdoors. Our app specializes in finding national parks to enjoy and mountains to climb. You will use what you know about React to complete this project. You will also need to flex your research skills to solve any blockers you run into.

## Starter Code
Fork the following repo as a starter for this project

- https://github.com/erics273/enjoy_the_outdoors_starter

## Basic Requirements
The website should include the following in order to be considered complete:

- **A National Parks Search Page** - The National Parks search page provides a user interface that allows the user to search for the park that is just right for them.  Data comes from a file on the server named `nationalparks.json` located in `public/data`.

- **Mountains Information Page** - The mountains information page provides a user interface that allows the user to explore the details of 48 different mountains. Data comes from a file on the server named `mountains.json` located in `public/data`.

> **NOTE** There are ample opportunities in this project to keep you busy and stretch your skills.  Just make sure the basic requirements above are met before you decide to tackle any optional features!!

## Implementation Details
Below you will find implementation requirements and details about the **National Parks search page**, **Mountains Information page**, **stretch goals**, and general implementation hints.

### National Parks Search Page 
This page will allow the user to search for national parks that they might be interested in.  The parks are provided to you in `nationalparks.json`. Spend some time examining this file.

Ultimately, the user would like to have two ways to search for a national park:
 - **By location** 
 - **By park type**

**Search by Location** - This option allows users to select the state/territory from a [dropdown](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select). Values for the state/territory dropdown will be provided for you in `locations.json`.  **You will know a park matches the location by comparing it to the park's State" property**. 

> **NOTE:** Search by Location is the most important search option and should be the highest priority to complete.

**Search by Park Type** - This option allows users to select a description from a [dropdown](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select). Values for the park type dropdown will be provided for you in `parktypes.json`.  **You will know a park matches the description by checking to see if the park's "LocationName" property ***includes*** the description**. 

One of the challenges will be how the user is presented with two search options populated with the appropriate values. Do you use [radio buttons](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/radio) to select the search type?  Do you use a [dropdown](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select) with the search types as [options](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/option)?

#### Nationa Parks Search Page Stretch Goals
Challenge yourself with some of the stretch goals below. **These stretch goals should be treated as the lowest priority tasks**

- Provide a View All National Parks option.
- Some, but not all National Parks, contain a **"Visit"** property that contains a URL to a page about the park. You can display the URL in a hyperlink (ex: [<a>](https://mdn.io/a) tag) along with park details so the user can click on it and visit the park's page from your list.  Make sure to open the visited page in a different tab/window!

#### IMPLEMENTATION HINTS

- Get the two search options to load their respective options before getting the actual search working. Options include:
- **Suggestion:** Get the "Search by Location" feature working first.
- When you are working on the "Search by Park Type", you need to make sure the two strings have the same casing when you search.  The easiest way to do this is to use the `String` objects [`.toLowerCase()`](https://mdn.io/toLowerCase)  (or [`.toUpperCase()`](https://mdn.io/toUpperCase) ) to make the strings the same case.

### Mountains Information Page
This page will provide a drop-down list of the 48 mountains listed in `mountains.json.` Make sure to spend time examining this file.

When the user selects a mountain, your page will display information about that mountain, including:

- Mountain Name
- Description
- Elevation
- Any other information you find interesting about the Mountain. 

> **NOTE:** This page will NOT allow the user to search mountains using any type of filter.

#### Mountain Information Page Stretch Goals
Challenge yourself with some of the stretch goals below. **These stretch goals should be treated as the lowest priority tasks**

- Display an image of the mountain along with the mountain information. 
- Impress the user by displaying the sunrise and sunset time "today" for any mountain along with the other mountain data.
  ```js

  //function that can "fetch" the sunset/sunrise times
  async function getSunsetForMountain(lat, lng){
      let response = await fetch(`http://api.sunrise-sunset.org/json?lat=${lat}&lng=${lng}&date=today`)
      let data = await response.json()
      return data
  }

  //Using the function to fetch the sunset/sunrise times for a specific mountain 
  getSunsetForMountain("44.320686", "-71.291742").then(sunsetData => {
      console.log(sunsetData.results)
  });
  ```

> NOTE(S): the lat and lng values are included in the mountain data. The times returned are in UTC are not adjusted for local summer variations. Label the output as UTC time when you display them or try to convert them to local time for the user. 
