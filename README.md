# Frontend - carbon footprint chart task

👋 Welcome to the Altruistiq front-end hiring task!

**Objective**

Create a chart animating carbon footprint per country throughout the years. The below chart is an example for world population (see for animated version. The provided Figma file shows the one-page app that you should build for this task.

![https://miro.medium.com/max/1600/1*37uCN6y1WyLukxwCadhWRw.gif](https://miro.medium.com/max/1600/1*37uCN6y1WyLukxwCadhWRw.gif)

**Requirements**

1. pixel perfect implementation of the provided Figma file as a Vue app
2. use data from the [Footprint network](https://data.footprintnetwork.org/#/api)
3. create the chart
4. calculate and show world total footprint on the page

**Stretch goals**

1. animate the sorting and bar length of the chart as per the provided example.
2. chart should be responsive, test by changing the window size (dragging)
3. cache data with timeout of 5 minutes, making sure upon reload the app conditionally uses stored data

**Get started**

1. [Get this Figma file](https://www.figma.com/file/WJ1BvQzvFchIFxo67iIywi/Altruistiq-frontend-hiring-task). The ... in the chart is a placeholder. The idea is that you show all the countries from the API response in the chart.

1. Clone this repo, then `npm i` and `npm run dev` to start a development app (uses Vite, Vue 3 and Vuex)

1. Use the 2 API calls provided in the store to get a list of countries and to get emission data per country per year. Do this for all countries. To chart the carbon footprint for a specific year, you need the `carbon` attribute from the response. Note that for some countries data for a specific year is missing.

   ```jsx
   // get all countries
   await this.dataStore.getCountries()

   // [
   //   {
   //       "id": 1,
   //       "version": null,
   //       "countryCode": "1",
   //       "countryName": "Armenia",
   //       "shortName": "Armenia",
   //       "isoa2": "AM",
   //       "score": "3A"
   //   },
   //   {
   //       "id": 2,
   //       "version": null,
   //       "countryCode": "2",
   //       "countryName": "Afghanistan",
   //       "shortName": "Afghanistan",
   //       "isoa2": "AF",
   //       "score": "3A"
   //   },
   //   ...
   // ]

   // get data for a single country by countryCode
   await this.getCountry({ countryCode: 229 })

   // [
   //    {
   //       "id": 4193,
   //       "version": null,
   //       "year": 1961,
   //       "countryCode": 10,
   //       "countryName": "Australia",
   //       "shortName": "Australia",
   //       "isoa2": "AU",
   //       "record": "EFConsPerCap",
   //       "cropLand": 0.521280004829556,
   //       "grazingLand": 2.81094109134558,
   //       "forestLand": 1.03202880039184,
   //       "fishingGround": 0.0509710310900806,
   //       "builtupLand": 0.0247025489319933,
   //       "carbon": 3.02800424434668,
   //       "value": 7.46792772093573,
   //       "score": "3A"
   //    },
   //    ...
   //]
   ```

1. Add and use fonts
   ```jsx
   @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600&display=swap');
   ```
