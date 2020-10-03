## React google autocomplete Personal Fork

  This is my personal fork of the react-google-autocomplete repo. I've forked this repo and made a small change in the source code to make it work smoothly with the [google-maps-react](https://github.com/fullstackreact/google-maps-react) project. When displaying an autocomplete field from this package and a Google map from the other package on the same page you receive an error due to both adding Google's places library JS scripts twice on the page. 
  
  Before adding a Google script to the page, react-google-autocomplete checks first to see if a script already exists, but the criteria for this check is specific to the url structure of this package. I've modified the source code so that the package checks to see if any script that is importing the Google Places library is already existing on the page. If so, this package won't add another script, since it too already relies on that library. This also allows for this package to be more compatible with other react packages that use the Google places library and may run into the same issues. Everything below this paragraph is from the original react-google-autocomplete repo.


<hr>

  This is a simple react component for working with google [autocomplete](https://developers.google.com/maps/documentation/javascript/examples/places-autocomplete)

## Install

`npm i react-google-autocomplete --save`

<hr>

As of version 1.2.4, you can now pass an `apiKey` prop to automatically load the Google maps scripts. The api key can be found in your [google cloud console.](https://developers.google.com/maps/documentation/javascript/get-api-key)

```js
<AutoComplete
  apiKey={YOUR_GOOGLE_MAPS_API_KEY}
  onPlaceSelected={() => 'do something on select'}
/>
```

Alternatively if not passing the `apiKey` prop, you can include google autocomplete link api in your app. Somewhere in index.html or somewhere else.

```html
  <script type="text/javascript" src="https://maps.googleapis.com/maps/api/js?key=[YOUR_API_KEY]&libraries=places"></script>
```

## Example

```js
import Autocomplete from 'react-google-autocomplete';

<Autocomplete
    style={{width: '90%'}}
    onPlaceSelected={(place) => {
      console.log(place);
    }}
    types={['(regions)']}
    componentRestrictions={{country: "ru"}}
/>
```

The component has one function called `onPlaceSelected`. The function gets invoked every time a user chooses location.
A `types` props means type of places in [google place API](https://developers.google.com/places/web-service/autocomplete#place_types). By default it uses (cities).
A [componentRestrictions](https://developers.google.com/maps/documentation/javascript/reference#ComponentRestrictions) prop by default is empty.
A [bounds](https://developers.google.com/maps/documentation/javascript/reference#AutocompleteOptions) prop by default is empty.
You also can pass any props you want to the final input. You can also set [fields](https://developers.google.com/maps/documentation/javascript/reference/places-service#PlaceResult) prop if you need extra information, now it defaults to basic data in order to control expenses.
The `options`(optional) prop is the optional configuration to your Autocomplete instance. You can see full options [here](https://developers.google.com/maps/documentation/javascript/places-autocomplete#add_autocomplete) 

## Contribution

If you would like to see something in this library please create an issue and I will implement it as soon as possible.
