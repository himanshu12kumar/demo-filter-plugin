-------------------------------------------------------- Use cases of multi/single select filter plugin ---------------------------------------

For creating the simple filter UI with drop down data.
--------------------------------------------------------------------
A jQuery-based plugin for creating dynamic filter UIs with multi-select or single-select dropdown functionality.

This plugin offers customization options such as searchability, select/deselect all options, clear all, and more, making it perfect for advanced filtering needs.

In this plugin you have feasibility to set your own icons for select/deselect all,clear all,drop down.

This plugin provide you a better dependency functionality among two or more multi/single select drop down filter. By using this plugin you can easily achieve the fast and smooth dependency functionality with reducing the database load also. Bcz in this plugin you can store all filter data at a time after that this plugin handle dependency automatically. It will display child dependent option according to selected parent option.

For making the dependency functionality among two or more drop down filter, This plugin reduce the backend server side dependency or load for making the ajax request and hitting the database again and again to fetch the dependent data.

If your appliaction is form submit based then after refreshing the page, This plugin provide you the feasibility to set the privious selected option.

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
	<div id="demo"></div>
------------------------------

2) Define your data and settings
   
=> For loading data in filter drop down follow below object structure.

=> demo_data key name (demo) must be same of element's ids name

=> demo object keys will be the value of selected option

=> demo object name will be the visuals text in UI

------------------------------------------------------------------
	const demo_data= {
                demo: {    
                    '101': { name: 'Process 1'},   
                    '102': { name: 'Process 2'},    
                    '103': { name: 'Process 3'},
                    '104': { name: 'Process 4'},
                    '105': { name: 'Process 5'}
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
              $("#demo").CustomDropDown({
                dropdownData: demo_data,
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

 
