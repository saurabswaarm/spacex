[![Netlify Status](https://api.netlify.com/api/v1/badges/43dbe794-d217-4c54-9706-e95c20d2555e/deploy-status)](https://app.netlify.com/sites/saurab-spacex/deploys)

# SpaceX Launches Tracker

This project was created using React, Material-UI, Typescript, Apollo, Graphql. Just run the project using `yarn start` or `npm start` to get started.

This is a simple SpaceX Launches Tracker that gives you a glimpse of information of past launches. the left side is the list of launches and the right side contains an information pane that gives the user more details about the launch. 

## Available Scripts

### `yarn start`

Runs the app in the development mode.\
Open [http://localhost:3000]

### `yarn test:e2e`

Launches the test runner with a headfull chrome. This script runs the test that was requested in the coding challenge. The test picks two random launches and then compares them and returns back to the previous screen. The test checks for certain components that should be loaded, and whether the current items being compared are the same as the ones selected.

### `yarn generate --watch`

This will run the code generator to generate the types before hand.

# Approach

### State Management

Given that this was a tiny project, I used React's Context for state management. Although it is a quick and dirty solution, a more standard solution like Redux would have allowed me to maintain a better project structure. Using Context did allow me to avoid prop drilling, and allowed me to keep the bulk of the logic in `App.tsx`

### Data Display

Given the project involved depicting a large amount of information, I felt that using tables to depict all the data would have been the optimal approach. Material-UI's `<datagrid>` seemed to be a good choice for this. I decided to split the screen into two sections, the first would contain a list of launches and the second would give the user more details about the launch that is currently selected. This helps conserve space, without compromising on how much data we can show.

### Filters

For the filters, two categories were provided, which were mission name and rocket name, hence I created two search fields for the same. I used an AND relationship between the two filters which allows one to filter by **mission** and further refine the entries via filtering by **rocket**

### Compare

For the compare button, I decided to firstly rig the table such that it can only select two entries at a time. If you select more than two entries the entry that was selected first gets deselected. Also the compare button is activated only when there are two entries selected, else it remains deactivated. In a production project I wouldn't do this as selection has other uses also, and they shouldn't be limitted to just two entries. but for this project, I wanted to try out something different hence I used this approach.

# Personal Notes

If I had more time I would have paid more attention to the styling of the application. I would have also paid more attention to the naming of components. I would also have liked to add better filtering, which read the fetched data and generated appropriate filters in advance to choose from rather than just having a text input or search field.

## Omission

I also couldn't get the ships section of the graphql api to work and hence I had to omit it. No matter what I did including the ships section would return a 400 bad request from the spaceX server.
