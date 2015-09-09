# quick-maps

## Map 1 - Using Source-Destination Latitude Longitude Map  

1. `plotRoute(arg)` method is provided in `MapServiceManager.js` file to plot a route between 2 locations by providing `latitude` and `longitude` of Source and Destination Locations on map.  
2. `plotRoute(arg)` method accepts an object as parameter that contains following properties:

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

where, `result` object of `successCallback` and `routeChangeCallback` Method contains following properties:

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

3.a Consider, you want to plot all possible routes between 2 locations with following `latitude` and `longitude`:
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
    },
    failureCallback : function(){
    	console.log('Route couldn't be plotted between given latitudes and longitudes.');
    },
    routeChangeCallback : function(result){
    	console.log('Duration :' + result.duration);
    	console.log('Distance :' + result.distance);
    };
    }
    mapServiceManager.plotRoute(options);
```

##Map 2 - Using Source-Intermediate-Destination Latitude Longitude Map   

1. `plotRoute(arg)` method is provided in `MapServiceManager.js` file to plot a route between 2 locations with Intermediate locations by providing `latitude` and `longitude` of Source, Destination and Intermediate Locations on map.  
2. `plotRoute(arg)` method accepts an object as parameter that contains following properties:

```
    var options = {
    	mapCanvas : 'map', //id of the HTML DIV element where map is to be plotted.
    	points : locArray, //array of Source, Destination and Intermediate Locations.
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

where, `result` object of `successCallback` and `routeChangeCallback` Method contains following properties:

```
    var resultMap = {
    	duration : '2 Hours 3 Mins', //duration of route in DRIVING mode
    	distance : '78 kms' //distance of route
    };
```
    	

and, 1st element of `locArray` is considered as Source Location and Last element as Destination Location. Each Object of `locArray` is of following type:

```
    var locObj = {
    		plcnam:'Amritsar', //Name of Location
    		lat:'28.1111111', //Latitude
    		long:'76.1111111' //Longitude 
    		};
```
    	

3. Example

3.a Consider, you want to plot all possible routes between Location 1 and Location 4 with Intermediate Locations are Locations Location 2 and 3, having following `latitude` and `longitude`:  
Location 1 : Latitude (31.6335441), Longitude (74.8701203)  
Location 2 : Latitude (31.3223978), Longitude (75.5734192)  
Location 3 : Latitude (28.6454414), Longitude (77.0907573)  
Location 4 : Latitude (19.0822507), Longitude (72.8812042)    
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
    plcObj	= {plcnam:'Intermediate 1',
        		 	   lat:'31.3223978',
        		 	   long:'75.5734192'}; 
    locObj[count] = plcObj;
    count++;
    plcObj	= {plcnam:'Intermediate 2',
        		 	   lat:'28.6454414',
        		 	   long:'77.0907573'}; 
    locObj[count] = plcObj;
    count++;
    plcObj = {plcnam:'Destination',
        		 	   lat:'19.0822507',
        		 	   long:'72.8812042'};	 
    locObj[count] = plcObj;
    count++;
        
    var options = {
    mapCanvas : 'map', //map is the id of HTML DIV element where route is to be plotted.
    points : locObj,
    successCallback : function(result){
    	console.log('Duration :' + result.duration);
    	console.log('Distance :' + result.distance);
    },
    failureCallback : function(){
    	console.log('Route couldn't be plotted between given latitudes and longitudes.');
    },
    routeChangeCallback : function(result){
    	console.log('Duration :' + result.duration);
    	console.log('Distance :' + result.distance);
    };
    }
    mapServiceManager.plotRoute(options);
```

##Map 3 - Using Source-Destination Location Map  

1. `plotRoute(arg)` method is provided in `MapServiceManager.js` file to plot a route between 2 locations by providing `latitude` and `longitude` of Source, Destination Locations on map.  
2. `plotRoute(arg)` method accepts an object as parameter that contains following properties:  

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

where, `result` object of `successCallback` and `routeChangeCallback` Method contains following properties:

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
    	

3. `getLatLngFrmLoc(arg)` method is provided in `MapServiceManager.js` file to get `latitude` and `longitude` of a given location.  
4. `getLatLngFrmLoc(arg)` method accepts an object as parameter that contains following properties:  

```
    var options = {
    	location : 'Kanpur', //Name of the Location whose Latitude and Longitude is to be calculated.
    	successCallback : function(result){
        	//Get result after plotting route successfully.
    		},
    	failureCallback : function(){
        	//Code to handle failure in plotting route goes here.
    		}
    	}
```    	

where, `result` object of `successCallback` method contains following properties:

```
    var result = {
    	address : 'Kanpur, Uttar Pradesh' //Fully Qualified name of location 
    	latitude : '26.4471737', //Latitude of location
    	longitude : '80.3383828' //Longitude of location
    };
```
    	

5. `getLatLngFrmLoc(arg)` and `plotRoute(arg)` methods can be used together to plot route between two location by providing their names.  

6. Example  

6.a Consider, you want to plot all possible routes between 'Delhi' and 'Mumbai'.  
6.b In order to use `getLaLngFrmLoc`, write following code:  

```
    //Get the Latitude and Longitude of Delhi.
    var srcLatLong = [];
    var options {
    location = 'Delhi';	
    successCallback = function(result){
    			srcLatoLong.address = result.address;
    			srcLatLong.lat = result.latitude;
    			srcLatLong.long = result.longitude;			
    },		
    failureCallback = function(){
    			console.log('Entered location is not valid.');
    }	
    }		
    mapServiceManager.getLatLongFrmLoc(options);

    //Get the Latitude and Longitude of Mumnbai.
    var dstLatLong = [];
    var options {
    location = 'Mumbai';	
    successCallback = function(result){
    			dstLatLong.address = result.address;
    			dstLatLong.lat = result.latitude;
    			dstLatLong.long = result.longitude;			
    },		
    failureCallback = function(){
    			console.log('Entered location is not valid.');
    }	
    }		
    mapServiceManager.getLatLongFrmLoc(options);
```
    	

6.c In order to use `plotRoute`, write following code:

```
    //Use srcLatLong and dstLatLong values to call plotRoute(args) method.

    var count = 0
    var locObj = [];
    var plcObj;
    plcObj	= {plcnam:srcLatLong.address,
        		 	   lat:srcLatLong.lat,
        		 	   long:srcLatLong.long}; 
    locObj[count] = plcObj;
    count++;
    plcObj	= {plcnam:dstLatLong.address,
        		 	   lat:dstLatLong.lat,
        		 	   long:dstLatLong.long}; 
    locObj[count] = plcObj;
        
    var options = {
    mapCanvas : 'map', //map is the id of HTML DIV element where route is to be plotted.
    points : locObj,
    successCallback : function(result){
    	console.log('Duration :' + result.duration);
    	console.log('Distance :' + result.distance);
    },
    failureCallback : function(){
    	console.log('Route couldn't be plotted between given latitudes and longitudes.');
    },
    routeChangeCallback : function(result){
    	console.log('Duration :' + result.duration);
    	console.log('Distance :' + result.distance);
    };
    }
    mapServiceManager.plotRoute(options);
 ```
 
 ##Map 4 - Using Source-Intermediate-Destination Location Map   
 
1. `plotRoute(arg)` method is provided in `MapServiceManager.js` file to plot a route between 2 locations with Intermediate locations by providing `latitude` and `longitude` of Source, Destination and Intermediate Locations on map.  
2. `plotRoute(arg)` method accepts an object as parameter that contains following properties:  

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

where, `result` object of `successCallback` and `routeChangeCallback` Method contains following properties:

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
    	

3. `getLatLngFrmLoc(arg)` method is provided in `MapServiceManager.js` file to get `latitude` and `longitude` of a given location.  
4. `getLatLngFrmLoc(arg)` method accepts an object as parameter that contains following properties:  

```
    var options = {
    	location : 'Kanpur', //Name of the Location whose Latitude and Longitude is to be calculated.
    	successCallback : function(result){
        	//Get result after plotting route successfully.
    		},
    	failureCallback : function(){
        	//Code to handle failure in plotting route goes here.
    		}
    	}
```    	

where, `result` object of `successCallback` method contains following properties:

```
    var result = {
    	address : 'Kanpur, Uttar Pradesh' //Fully Qualified name of location 
    	latitude : '26.4471737', //Latitude of location
    	longitude : '80.3383828' //Longitude of location
    };
```
    	

5. `getLatLngFrmLoc(arg)` and `plotRoute(arg)` methods can be used together to plot route between two location by providing their names.  

6. Example  

6.a Consider, you want to plot all possible routes between 'Delhi' and 'Mumbai' with 'Pune' as intermediate Location.
6.b In order to use `getLaLngFrmLoc`, write following code:  

```
    //Get the Latitude and Longitude of Delhi.
    var srcLatLong = [];
    var options {
    location = 'Delhi';	
    successCallback = function(result){
    			srcLatoLong.address = result.address;
    			srcLatLong.lat = result.latitude;
    			srcLatLong.long = result.longitude;			
    },		
    failureCallback = function(){
    			console.log('Entered location is not valid.');
    }	
    }		
    mapServiceManager.getLatLongFrmLoc(options);

    //Get the Latitude and Longitude of Pune.
    var intLatLong = [];
    var options {
    location = 'Pune';	
    successCallback = function(result){
    			intLatLong.address = result.address;
    			intLatLong.lat = result.latitude;
    			intLatLong.long = result.longitude;			
    },		
    failureCallback = function(){
    			console.log('Entered location is not valid.');
    }	
    }		
    mapServiceManager.getLatLongFrmLoc(options);

    //Get the Latitude and Longitude of Mumnbai.
    var dstLatLong = [];
    var options {
    location = 'Mumbai';	
    successCallback = function(result){
    			dstLatLong.address = result.address;
    			dstLatLong.lat = result.latitude;
    			dstLatLong.long = result.longitude;			
    },		
    failureCallback = function(){
    			console.log('Entered location is not valid.');
    }	
    }		
    mapServiceManager.getLatLongFrmLoc(options);
```
    	

6.c In order to use `plotRoute`, write following code:  

```
    //Use srcLatLong and dstLatLong values to call plotRoute(args) method.

    var count = 0
    var locObj = [];
    var plcObj;
    plcObj	= {plcnam:srcLatLong.address,
        		 	   lat:srcLatLong.lat,
        		 	   long:srcLatLong.long}; 
    locObj[count] = plcObj;
    count++;
    plcObj	= {plcnam:intLatLong.address,
        		 	   lat:intLatLong.lat,
        		 	   long:intLatLong.long}; 
    locObj[count] = plcObj;
    count++;
    plcObj	= {plcnam:dstLatLong.address,
        		 	   lat:dstLatLong.lat,
        		 	   long:dstLatLong.long}; 
    locObj[count] = plcObj;
        
    var options = {
    mapCanvas : 'map', //map is the id of HTML DIV element where route is to be plotted.
    points : locObj,
    successCallback : function(result){
    	console.log('Duration :' + result.duration);
    	console.log('Distance :' + result.distance);
    },
    failureCallback : function(){
    	console.log('Route couldn't be plotted between given latitudes and longitudes.');
    },
    routeChangeCallback : function(result){
    	console.log('Duration :' + result.duration);
    	console.log('Distance :' + result.distance);
    };
    }
    mapServiceManager.plotRoute(options);
```

##Map 5 - Using Location Map  

1. `plotLocation(arg)` method is provided in `MapServiceManager.js` file to plot a Location on map.  
2. `plotLocation(arg)` method accepts an object as paramter that contains following properties:  

```
    var options = {
    	mapCanvas : 'map',
    	location : 'Amritsar',
    	successCallback : function(result){
    		//Get result after plotting map successfully.
    	},
    	failureCallback : function(){
    		//Code to handle failure in plotting map goes here.
    	}
    }
```    	

where, `result` object of `successCallbackMethod` contains following properties:

```
    var result = {
    	latitude : '20.123456',
    	longitude : '78.123456',
    	location : 'Amritsar,Punjab,India'
    };
```
    	

3. Example  

3.a Consider, you want to plot a location with keyword saket on map and after location is plotted you want to display its latitude,longitude & Fully Qualified Location Name on map on console.  
3.b In order to use `plotLocation`, write following code:  

```
    var options = {
    mapCanvas : 'map', //map is the id of HTML DIV element where you want to plot your map.
    location : 'Saket',
    	successCallback = function(result){
    		console.log('Latitude : ' + result.latitude);
    		console.log('Longitude : ' + result.longitude);
    		console.log('Formatted Name : ' + result.location);	
    	},
    	failureCallback = function(){
    		 console.log('Entered location couldn't be plotted on map.');
    		 
    	}
    }
    mapServiceManager.plotLocation(options);
```    	









