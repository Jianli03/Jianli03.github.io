---
layout: single
title: "Use Bower To Manage Front-End Dependencies"
---
{% include base_path %}
 
## What is Bower
![image-right](/images/bower.jpg){: .align-right}  
Bower — a package manager for the web.  

> "Web sites are made of lots of things — frameworks, libraries, assets, and 
> utilities. Bower manages all these things for you."  
  


## Why Use Bower
Recently I have been working on some website development projects. 
I found that it was time consuming and error prone to manually manage third party packages like jQuery, Bootstrap, Moderniz, which generally means googling and downlaoding those packages. In the further, repeating process all over again might be needed for updating. I was pretty sure there is a way similar to how we manage Java dependency using Maven or Grandle. Therefore, I leart and used Bower to manage components of the front end. Bower is very handy to install the right versions of the packages you need and manage their dependencies.  


To intall a package would like this:
    $ bower install jquery

To keep a package up to date would like this:
    $ bower update jquery  

How simple it is! So let us go through some examples to learn how to handle third party packages matters using a few bower commands.
By the way, Node's NPM is an altertive you can choose to achieve the simplicity.

### Install Bower
    $ npm install -g bower 	// -g means globel   
    $ bower --version 		// check if the installation is ok  
    1.7.19  				// version number   

### Getting Started

##### Create a Project.

    $ mkdir bower-in-action
    $ cd bower-in-action

##### Initialize the Project.
Bower keeps track of dependency using a file named "package.json"  that contain information about a project and a list of packages it uses. create this file by intializae a project.  

    $ bower init   
    
You will be answering a list of questions and answers will form your “bower.json” file as following:
  
    {    
      "name": "bb_boot",  
      "version": "0.0.1",  
      "authors": [  
        "james <james@qq.com>"  
      ],  
      "moduleType": [  
        "amd"  
      ],  
      "license": "MIT",  
      "ignore": [  
        "**/.*",  
        "node_modules",  
        "bower_components",  
        "js/lib",  
        "test",  
        "tests"  
      ],
      "dependencies": {  
      }
    }
     
##### Install jQuery and Bootstrap packages
    $ bower install jquery
    $ bower install bootstrap

A directory named ower_components is created after the installation.The package files of jquery and bootstrap are downloaded and stored in this folder. 

##### Search a package
Use this online [Search Bower packages](http://bower.io/search/)  
or  
    
    $ bower search bootstrap  

Searching on the Bower's page is more straightforward.  
    
    $ bower uninstall jquery
     
##### Install with Save
    
    $ bower install jquery --save  
    
bower downloads the latest jquery to your js/lib folder
--save write the configures to bower.json：

    "dependencies": {  
      "jquery": "~2.1.4"  
    }  
  
##### Pakage Info
if we would like to find the package version:  

    $ bower info jquery    

    
You can down grade the version by write version number into this bower.json like following:  

    "dependencies": {
       "jquery": "~1.11.3"
    }
and than  
    
    $ bower update  
    
after that, jquery version has been changed to 1.11.3
 
##### Uninstall jQuery 
    $ bower uninstall jquery

    {  
      "name": "jquery-in-action",  
      "version": "0.0.0",  
      "authors": [  
        "james <james@qq.com>"  
      ],  
      "description": "test bower using jquery & bootstrap",  
      "keywords": [  
        "jquery",  
        "bootstrap"  
      ],  
      "license": "MIT",  
      "dependencies": {  
        "bootstrap": "latest",  
        "font-awesome": "latest",  
        "animate.css": "latest",  
        "angular": "latest"      
      },
      "devDependencies": {
        "angular": "~1.3.8"
      }
    }
   
  
To be aware there are to kinds of Dependencies. One is named "dependencies"  and anther is named "devDependencies". They are repereneting dependencies in Production Env and Development Env respectively. Those dependencies can be saved respectively like following:   
  
  
      $ bower install jquery --save    // add to devDependencies  
      $ bower install angular --save-dev		//add to devDependencies  


### Use Bower

In the following example we are add dependencies into a webpage managed by bower：

    <!-- index.html -->  
    <!doctype>  
    <head>
      <link rel="stylesheet" href="libs/bootstrap/dist/css/bootstrap.min.css">  
      <link rel="stylesheet" href="libs/font-awesome/css/font-awesome.min.css">  
      <link rel="stylesheet" href="libs/animate.css/animate.min.css">  
      
      <script src="libs/jquery/jquery.min.js"></script>  
      <script src="libs/bootstrap/dist/js/bootstrap.min.js"></script>  
      <script src="libs/angular/angular.min.js"></script>    
    </head>    
 
#### .bowerrc file

.bowerrc is a JSON file for Bower configuration. It can be created after the root directory is created for the project.
In this file we can spefiy bower packages installation directory, registry server info：  
  
    {  
      "directory": "bower_components",  
      "analytics": false,  
      "timeout": 120000,  
      "registry": {  
        "search": [  
          "http://localhost:8000",  
          "https://bower.herokuapp.com"  
        ]  
      }  
    }  
 

To sum up, Bower makes it faster and easier for you to manage third party packages.
 
[Go back]({{ site.baseurl }}/index.html)