-------------------------------------------------------- Use cases of multi/single select filter plugin ---------------------------------------

For creating the simple filter UI with drop down data.
--------------------------------------------------------------------
A jQuery-based plugin for creating dynamic filter UIs with multi-select or single-select dropdown functionality.

This plugin offers customization options such as searchability, select/deselect all options, clear all, and more, making it perfect for advanced filtering needs.

In this plugin you have feasibility to set your own icons for select/deselect all,clear all,drop down.

This plugin provide you a better dependency functionality among two or more multi/single select drop down filter. By using this plugin you can easily achieve the fast and smooth dependency functionality with reducing the database load also. Bcz in this plugin you can store all filter data at a time after that this plugin handle dependency automatically. It will display child dependent option according to selected parent option.

For making the dependency functionality among two or more drop down filter, This plugin reduce the backend server side dependency or load for making the ajax request and hitting the database again and again to fetch the dependent data.

If your appliaction is form submit based then after refreshing the page, This plugin provide you the feasibility to set the previous selected option.

This plugin provide the feasibility to users to convert the drop down filter in single or multi select.

> Prerequisites

1) Include The plugin's JS and CSS files.

2) Include jQuery library.

> Installation

1) Create one html page and put below html code for storing the filter UI.
2) Include the required files in your HTML.

`<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/himanshu12kumar/ajax-multiselect-drop-down-filter@vv1.0.4/drop-downmanager.min.css">`

`<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.7.1/jquery.min.js"></script>`

`<script src="https://cdn.jsdelivr.net/gh/himanshu12kumar/ajax-multiselect-drop-down-filter@vv1.0.4/drop-downmanager.min.js"></script>`

> Usage

1) Create a placeholder element in HTML where the dropdown UI will be rendered
   
------------------------------
	<div id="first"></div>         // Be sure id's name should be plain text only, don't use underscore _ hyphen - etc
 	<div id="second"></div>
------------------------------

2) Define your data and settings
   
=> For loading data in filter drop down follow below object structure.

=> demo_data key name (demo) must be same of element's ids name

=> demo object keys will be the value of selected option

=> demo object name will be the visuals text in UI

------------------------------------------------------------------
	const first_data= {
                first: {    
                    '101': { name: 'Process 1'},   
                    '102': { name: 'Process 2'},    
                    '103': { name: 'Process 3'},
                    '104': { name: 'Process 4'},
                    '105': { name: 'Process 5'}
                }
            };

     	  const second_data= {
                second: {    
                    's_101': { name: 'second 1',first: ['101','104']},   
                    's_102': { name: 'second 2',first: ['105','103','102']},    
                    's_103': { name: 'second 3',first: ['104','103']},
                    's_104': { name: 'second 4',first: ['105']},
                    's_105': { name: 'second 5',first: []}
                }
            };
            
             const filter_settings = { 
                          'Searchable': true,
                          'SelectAll': true,
                          'SelectAllImg': 'imagePath....',
                          'DeselectAll': true,
                          'DeselectAllImg': 'imagePath....',
                          'ClearAll': true,
                          'ClearAllImg': 'imagePath....',
                          'DropDownIcon': true,
                          'DropDownIconImg': 'imagePath....',
                          'Counting': true,
                          'FontSize': 14,
                          'IconSize': 13,
                          'DropDownSize': 275,
                          'SelectFeature': 'multi/single'     
                };
---------------------------------------------------------------------------------

=> Either you can put 'multi' or 'single' as per recomended

3) Initialize the dropdown with your data and settings:

	=> dropdownData will store the drop down data object name

  => settings will store the filter setting object name
  
          	$(document).ready(function() {
	   
	              $("#first").CustomDropDown({
	                dropdownData: first_data,
	                settings: filter_settings
	              });

		       $("#second").CustomDropDown({
	                dropdownData: second_data,
	                settings: filter_settings
	              });
	      
            	});
    
> Available Features

=> These above steps provide you the basic structure of filter with below features and functionality.
	
  1. Searching functionality
	
  2. Select option
	
  3. Deselect option with 2 types
	
  4. Select all functionality
	
  5. Deselect all functionality
	
  6. Clear all functionality
	
  7. Counting visuals
	
  8. Selected value will upside and Deselected value will downside
	
  9. Different visuals with hover effect in drop down options

> Demo

=======> You can see the demo here
https://himanshu12kumar.github.io/demo-filter-plugin/

> Pass selected option
 => After refreshing the page if you want to display previous selected option, you need to pass the list of selected values

	const selectedprocess = ['101','102'];
 
	$(document).ready(function() {
              $("#demo").CustomDropDown({
                dropdownData: demo_data,
		selectedItem: selectedprocess,
                settings: filter_settings
              });
            });
> Convert drop down into multi/single select

	'SelectFeature': 'multi'       // you need to pass this in settings object for multi select drop down
 	'SelectFeature': 'single'      // for single select drop down

> Dependency settings

 => You need to maintain a dependency object with key-value pair

 	const dropdownDependency = {
            'first_second': second_data,
            'filter_settings': filter_settings     // If there is no dependency among 2 or more filter then you no need to provide this setting option here
        }                                      // If there is any dependency among 2 or more filter, you have to provide it at any cost

 => Here how you can define dependency object

 Object name you must keep 'dropdownDependency' only you can't change

 Keys name will be defined like that if you have 2 drop down filter 'first' and 'second' , and second is depends on first

 keys name will be 'first_second' for second flter and value for 'first_second' will be data object created for second filter.

 => Here how you can define data object for second filter
 
	const second_data= {
		second: {    
		    's_101': { name: 'second 1',first: ['101','104']},   // it's means 's_101' belongs to '101' and '102'
		    's_102': { name: 'second 2',first: ['105','103','102']},    
		    's_103': { name: 'second 3',first: ['104','103']},
		    's_104': { name: 'second 4',first: ['105']},
		    's_105': { name: 'second 5',first: []}      // it's means 's_105' didn't belongs to any first option
		}
	    };

> Use case of 3 filter

 => If you have 3 filter 'first', 'second', 'third' and if 'second' depends on 'first' and 'third' depends on both 'second' and 'first'

 => How you can define dependency object with key-value
 
	const dropdownDependency = {
            'first_second': second_data,            // key name for 'second' filter will be 'first_second'
	    'first_second_third': third_data        // key name for 'third' filter will be 'first_second_third'
            'filter_settings': filter_settings
        } 

 => If 'third' filter is depends only on 'second' then.

 	const dropdownDependency = {
            'first_second': second_data,            // key name for 'second' filter will be 'first_second'
	    'second_third': third_data        // key name for 'third' filter will be 'second_third'
            'filter_settings': filter_settings
        }

 => How you can define data object for 'third' filter if 'third' filter depends on both 'first' and 'second'.

 	const third_data= {
		third: {    
		    't_101': { name: 'third 1',first: ['101','104'],second: ['s_101']}, 
		    't_102': { name: 'third 2',first: ['105','103','102'],second: ['s_103']},    
		    't_103': { name: 'third 3',first: ['104','103'],second: ['s_103','s_105']},
		    't_104': { name: 'third 4',first: ['105'],second: ['s_104','s_102']},
		    't_105': { name: 'third 5',first: [],second: ['s_105']} 
		}
	    };

=> Now how you can initialize the drop down in dependency case

	$(document).ready(function() {
	   
	      $("#first").CustomDropDown({
		dropdownData: first_data,
		dependency: ['first_second','first_second_third'], //It's means first belongs to 'second' and 'third' filter so pass key name for 'second' and 'third' filter
		depsettings: 'filter_settings'  // If dependency is there among filter so you need to pass this params also
		settings: filter_settings
	      });

	       $("#second").CustomDropDown({
		dropdownData: second_data,
  		dependency: ['first_second_third'],
    		depsettings: 'filter_settings'
		settings: filter_settings
	       });
	      
        });
     
