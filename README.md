# Data-Dump
Selfhosted service for data capturing.


## The Problem
Handling data requiers building out a user interface and configuring graphs and other to make it look good as well as making sure both backend and frontend communicate in the same way

## The Solution
This project aims to solve the above problem.

The project involves 3 parts:
- [Throwing](#throwing)
- [Capturing](#capturing)
- [Storage and retreval](#storage-and-retreval)

This project is supposed to provide a selfhosted data capturing webserver and a complementary user interface.
The idea is that when you have some data you want to manage, you simply spin up the service and "throw" all your data at it and after a small amount of setup, it should handle the rest.


### Throwing
Process done by any external applicaion where it sends any data in any format* at the capturing service

The key thing about throwing is that it does not require the data to be formatted*. Wich is one of the main points of the entire project. Having a application integrate into Date-Dump should be as simple as
```py
import request
request.post("127.0.0.1:6050", json={"speed":"1.75"})
```

Data is then processed by the capture service and converted to a standadized format for storage. 



### Capturing
The capturing services's main job of taking whatever is thrown at it and converting it to usable data

The service should accept as many types of inputs as possible over both http and ws, some examples of input methods are:
- json
- text
- form
- url args
The more input methods implemented, the better. But at the earlier stages like right now, only json and text will be focused on.


#### Processing

Processing is when the capturing services takes the inputed data and converts it to a known formatting that all other parts of the service can use.

This does require *some* setup as you need to pick the right data processing method for the data given to the capturing service. 
In the case that there doesn't exist any premade processors for the format you are giving to the capturing service you are given the option to write your own custom processor.


### Storage and retreval

#### Storage
Storage utelizes an 
