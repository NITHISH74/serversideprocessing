# Design a Website for Server Side Processing

## AIM:
To design a website to perform mathematical calculations in server side.

## DESIGN STEPS:

### Step 1:
To start the server and open theia IDE. 

### Step 2:
Create a folder and Start the django project in that folder.
### Step 3:
Use views.py to execute the coding in serverside.

### Step 4:

Mention the path of the website in urls.py.

### Step 5:
Write a HTML and CSS code for mathematical calculator.


### Step 6:

Publish the website in the given URL.

## PROGRAM :
## HTML code:
```
<!DOCTYPE html>
<html>
<head>
    <meta charset='utf-8'>
    <meta http-equiv='X-UA-Compatible' content='IE=edge'>
    <title>Mathematical calculator</title>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
    <link rel='stylesheet' type='text/css' media='screen' href='main.css'>

</head>
<style>
    .id{
        text-align: center;
        font-size: 30px;
        background-color: blanchedalmond;
        margin-left: 200px;
        margin-right: 200px;
        padding-bottom: 25px;
    }
    body{
          background: linear-gradient(75deg,blue,violet);

    }
    .volume{
        background-color:#3DA4E6;
        font-size: 15px;
        color: black;
    }
    footer{
        background-color: sandybrown;
        text-align: center;
        font-size: 20px;
        margin-top: 15px;  
    }
        h2{
            text-align: center;
            font-size: 50px;
            color: aquamarine;
        }
  
</style>
<body>
    <div class="container">
            <H2>Welcome to server side programming </H2>

    <div class="id">
    <h1>Area of the rectangle</h1>
    <form method="POST">
        {% csrf_token %}
        Length=<input type="text" name="length" value="{{l}}">Meters</input><br/>
        Breadth=<input type="text" name="breadth" value="{{b}}">Meters</input><br/>
        <input class="volume" type="submit" value="CalculationArea"></input><br/>
        Area=<input type="text" name="Area" value={{area}} readonly></input>Meters<sup>2</sup><br/>

    </form>
            </div>
              <div class="id">
    <h1>Volume of the Cylinder</h1>
    <form method="POST">
        {% csrf_token %}
        Radius=<input type="text" name="radius" value="{{r}}">Meters</input><br/>
        Height=<input type="text" name="height" value="{{h}}">Meters</input><br/>
        <input class="volume" type="submit" value="CalculationVolume"></input><br/>
        Volume =<input type="text" name="volume" value={{volume}} readonly></input>Meters<sup>3</sup><br/>
    </form>
            </div>
        </div>
</body>
<footer>The server side Calculator was developed by NITHISHWAR.</footer>
</html>


```
## URLS page:
```
"""calculations1 URL Configuration

The `urlpatterns` list routes URLs to views. For more information please see:
    https://docs.djangoproject.com/en/3.1/topics/http/urls/
Examples:
Function views
    1. Add an import:  from my_app import views
    2. Add a URL to urlpatterns:  path('', views.home, name='home')
Class-based views
    1. Add an import:  from other_app.views import Home
    2. Add a URL to urlpatterns:  path('', Home.as_view(), name='home')
Including another URLconf
    1. Import the include() function: from django.urls import include, path
    2. Add a URL to urlpatterns:  path('blog/', include('blog.urls'))
"""
from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('areaofrectangle/',views.areacalculation,name="areaofrectangle"),
]
```
## views.py page:
```
from django.shortcuts import render

# Create your views here.
def areacalculation(request):
    context={}
    if request.method =='POST':
        l = request.POST.get('length','0')
        b = request.POST.get('breadth','0')
        area = int(l) * int(b)
        context['area'] =area
        context['l'] =l
        context['b'] =b

    if request.method =='POST':
        r = request.POST.get('radius','0')
        h = request.POST.get('height','0')
        volume =  3.14159 * int(r) * int(r) * int(h)
        context['volume'] =volume
        context['r'] =r
        context['h'] =h

    return render(request,'mathapp/area.html',context)

```

## OUTPUT:

### Area of the rectangle:

### Volume of the cylinder:


## Result:
A website to perform mathematical calculations in server side is created.



