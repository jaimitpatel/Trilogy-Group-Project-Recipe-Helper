![Recipe_Helper (1)](https://user-images.githubusercontent.com/3880463/148457499-353ab44b-08cf-4f00-bb88-ce9c0e410bd1.png)

![GitHub contributors](https://img.shields.io/github/contributors/charlestietjen/Trilogy-Group-Project-1)
![GitHub last commit](https://img.shields.io/github/last-commit/Charlestietjen/Trilogy-Group-Project-1)

### Links:

<li> Deployed Website: https://jaimitpatel.github.io/Trilogy-Group-Project-Recipe-Helper/ <br>
<li> Github : https://github.com/jaimitpatel/Trilogy-Group-Project-Recipe-Helper


## About the Project:
The main function of this site is to help users search for randomized recipies and cocktails. <br>
The user has the ability to choose a specific type of cuisine that they would like from a dropdown menu, <br> 
and the Recipe Helper would populate 20 different choices that the user could cycle through. <br>
The user also has the option to select a randomized cocktail to pair with their recipe of choice. <br>
This is done using two different API's; [Edamam](https://developer.edamam.com/edamam-docs-recipe-api) , and [CocktailDB](https://www.thecocktaildb.com/api.php)




## Project Requirements:
```python
- Use a CSS framework other than Bootstrap.
- Be deployed to GitHub Pages.
- Be interactive (i.e: accept and respond to user input).
- Use at least two server-side APIs.
- Does not use alerts, confirms, or prompts (use modals).
- Use client-side storage to store persistent data.
- Be responsive.
- Have a polished UI.
- Have a clean repository that meets quality coding standards (file structure, naming conventions, follows best practices for class/id-naming conventions, indentation, quality comments, etc.).
-Have a quality README (with unique name, description, technologies used, screenshot, and link to deployed application).
```

## Summary on Application:
```python
- Page loads
- User enters a cuisine category into the form field
    - The form field assists the user by autocompleting to valid entries
- User clicks on the meal button
    - API call fills an array w/meal objects of the chosen cuisine from edamam
    - A modal is presented to the user with information about a recipe
    - The user may click "next" to view the next index in the array
    - Clicking "Select" locks in the currently viewed recipe
    - The modal closes on clicking "Select" or clicking outside the modal
- User clicks on the cocktail button
    - API call fills an array w/drink items
    - Second API call to grab the first index in the array
    - A modal is presented with information grabbed in the second call
    - The user may click "next" to view the next index in the array
    - Each next will require a new API call
    - Clicking select locks in the currently viewed recipe
    - The modal closes on clicking "Select" or clicking outside the modal)
```
## API Details:
### Edamam:
In order to use this API, we used an async function to pull data from Edamam's API Endpoints using 3 different parameters; <br>
##### Random: <li> This string is set to true, in order to always give a random set of recipes, instead of the same 20. </li>
##### Type: <li> This is set to 'Main Course', because we do not want the api to pull results for any drinks, thus allowing it to only pull food items. </li>
##### CuisineType: <li> this is set as a variable in the function. This is the main part of the script, as this incorporates user input and allows users to select the cuisine type they would like. <br>
  
 This is the function that was used to pull data from the Edamam API:
```javascript
async function fetchMeal(){
  let APP_ID = ""
  let APP_KEY = ""
  let TYPE = cuisineType
  let response = await fetch ('https://api.edamam.com/api/recipes/v2?type=public&app_id=' + APP_ID + '&app_key=' + APP_KEY + '&random=true&dishType=Main%20course&cuisineType=' + TYPE)
  if(response.ok){
    let data = await response.json()
    recipeData = data;
    fillRecipeModal(0);
  } else {
    badResponseModal();
  };
};
```
##### The Request URL: https://api.edamam.com/api/recipes/v2?type=public&app_id=' + APP_ID + '&app_key=' + APP_KEY + '&q=' + '&random=true&dishType=Main%20course&cuisineType=' + TYPE


### CocktailDB:
This API was very straight forward, as it only allowed one random search per call. Which means that if the user wanted to <br>
try another recipe, they would have to make another API call request. <br>

This is the function that was used to pull data from the CocktailDB API:
```javascript
async function fetchCocktail() {
  let API_KEY = "1"
  let response = await fetch ('https://www.thecocktaildb.com/api/json/v1/1/random.php')
  let data2 = await response.json()
  cocktailData = data2;
  resultCocktailDirectionsel.innerText = cocktailData.drinks[0].strInstructions;
  resultSection.classList.remove('hide');
  setCocktailIngredients();
```
##### Endpoint: https://www.thecocktaildb.com/api/json/v1/1/random.php

### Diagrams:
    
![Screenshot 2022-01-06 154454](https://user-images.githubusercontent.com/3880463/148454061-aa5c04ff-209e-424a-bc14-a987c465990c.png)
![Screenshot 2022-01-06 154820](https://user-images.githubusercontent.com/3880463/148454043-698ee48c-98d5-4a8d-b3c1-6dd2591de9f0.png)
![Screenshot 2022-01-06 154722](https://user-images.githubusercontent.com/3880463/148454055-c7c2aa03-c080-4d06-895e-956892ffd624.png)
![Screenshot 2022-01-06 170548](https://user-images.githubusercontent.com/3880463/148458898-d68b9076-b4df-45b8-b09b-9f374a8f490b.png)


## Technology Used:
<li> Edamam API
<li> CocktailDB Api
<li> Bootstrap 5
<li> Google Fonts
<li> Animate.Style
<li> JQuery
  







## Contributors:
1. [Charles](https://github.com/charlestietjen) (Page Logic)
2. [Abi](https://github.com/abi-2021) (CSS and Styling)
3. [Saj](https://github.com/sajees89) (Page Logic)
4. [Jaimit](https://github.com/jaimitpatel) (API Information)
<br>
©2021 All Rights Reserved.

