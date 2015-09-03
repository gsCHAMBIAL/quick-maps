# quick-maps

## Map 1 - Using Source-Destination Latitude Longitude Map

1. plotRoute(arg) method is provided in MapServiceManager.js file to plot a route between 2 locations by providing latitude and longitude of Source and Destination Locations on map.
2. plotRoute(arg) method accepts an object as parameter that contains following properties:

    ```
    var options = {
    	mapCanvas : 'map', //id of the HTML DIV element where map is to be plotted.
    	points : locArray, //array of Source and Destination Location.
    	successCallback : function(result){
        	//Get result after plotting route successfully.
    		},
    	failureCallback : function(){
        	//Code to handle failure in plotting route goes here.
    		},
    	routeChangeCallback : function(result){
    		//Code to handle change in selected route in case of multiple routes are plotted on map.
    		}
    	}
    ```	

where, result object of `successCallback` and `routeChangeCallback` Method contains following properties:

  ```
    var resultMap = {
    	duration : '2 Hours 3 Mins', //duration of route in DRIVING mode
    	distance : '78 kms' //distance of route
    };
  ```
    	

and, `locArray` is an array of objects of following type:

  ```
    var locObj = {
    		plcnam:'Amritsar', //Name of Location
    		lat:'28.1111111', //Latitude
    		long:'76.1111111' //Longitude 
    		};
  ```
    	

3. Example

3.a Consider, you want to plot all possible routes between 2 locations with following latitude and longitude:
Location 1 : Latitude (31.6335441), Longitude (74.8701203)
Location 2 : Latitude (28.6454414), Longitude (77.0907573)
3.b In order to use `plotRoute`, write following code:

  ```
    var count = 0
    var locObj = [];
    var plcObj;
    plcObj	= {plcnam:'Source',
        		 	   lat:'31.6335441',
        		 	   long:'74.8701203'}; 
    locObj[count] = plcObj;
    count++;
    plcObj = {plcnam:'Destination',
        		 	   lat:'28.6454414',
        		 	   long:'77.0907573'};	 
    locObj[count] = plcObj;
    count++;
        
    var options = {
    mapCanvas : 'map', //map is the id of HTML DIV element where route is to be plotted.
    points : locObj,
    successCallback : function(result){
    	console.log('Duration :' + result.duration);
    	console.log('Distance :' + result.distance);
    };
    failureCallback = function(){
    	console.log('Route couldn't be plotted between given latitudes and longitudes.');
    };
    routeChangeCallback = function(result){
    	console.log('Duration :' + result.duration);
    	console.log('Distance :' + result.distance);
    };
    }
    mapServiceManager.plotRoute(options);
   ``` 	


