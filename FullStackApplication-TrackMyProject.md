# Introduction
- Hello everybody! In this Full Stack Tutorial we will build a simple project tracking application with dashboards.
- We will use  Next.js and Wundergraph to build this project
 
### Getting started
- Please clone this starting repository [start repo link]
- Make sure you have *docker* installed and running and you also need latest version of *node*.
- Run following commands After a while, a new browser tab will open, and you can start exploring the application. If no tab is open, navigate to http://localhost:3000.
```js
npm install && npm start
```
### How does the app work?

The app has 5 stages and 6 actions with following rules
- Rows define actions, E.g., Delete a project.
- Columns represent the *Stages* of the project.
- 3rd row, 5th columns state: A project can be *Deleted* in *Archived* stage.


|           	| New 	| In Progress 	| Completed 	| Cancelled 	| Archived 	|
|-----------	|-----	|-------------	|-----------	|-----------	|----------	|
| Create    	| Yes 	| No          	| No        	| No        	| No       	|
| Update    	| Yes 	| Yes         	| No        	| No        	| No       	|
| Delete    	| No  	| No          	| NO        	| No        	| Yes      	|
| Cancel    	| No  	| Yes         	| No        	| No        	| No       	|
| Archive   	| Yes 	| Yes         	| Yes       	| Yes       	| No       	|
| Unarchive 	| No  	| No          	| No        	| No        	| Yes      	|


## Building Front end Components
This section covers major components we will design
 - Header
 - Siderbar
 - Project screens
### App layout
 - Define a generic layout with *Header* and *Sidebar*
### Design dashboards
 - Top dashboards counts
 - Top 5 - Expensive Projects
 - Projects - Status
## Routing
  - define routing and nested routes
## Wundergraph & Business Logic 
- Display projects by status and refetch
- CRUD logic
  - Fetch projects by *Status*
  - Create project screen
  - Edit project screen
  - Delete project
- Dashboard workings
  - Define logic to calculate dashboards
## Final thoughts

