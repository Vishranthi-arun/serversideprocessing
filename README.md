# Design a Website for Server Side Processing

## AIM:
To design a website to perform mathematical calculations in server side.

## DESIGN STEPS:

### Step 1:
Create a new Angular project.

### Step 2:
Inside project create app called mathapp.

### Step 3:
Create a html called area.html

### Step 4:
Do the mathematical part in views.py

### Step 5:
Give the urls in urls.py

### Step 6:
Publish the website in the given URL.

## PROGRAM :
### area.html:
```
<!DOCTYPE html>
<html>
<head>
    <meta charset='utf-8'>
    <meta http-equiv='X-UA-Compatible' content='IE=edge'>
    <title>Page Title</title>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
    
</head>
<style>
    *{
        box-sizing: border-box;
        font-family:'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif
    }

    body{
    background-color: rgb(215, 233, 164);
    }

    .container{
    width: 1080px;
    height: 350px;
    margin-top: 100px;
    margin-left: auto;
    margin-right: auto;
    border-radius: 25px;
    border: 10px solid rgb(151, 92, 117);
    box-shadow: inset 0 0 15px rgb(202, 121, 155);
    background-color:rgb(192, 120, 150);
    }
    h1{
        text-align: center;
        padding-top: 15px;
    }
    .calculate{
        padding-top: 10px;
        padding-bottom: 10px;
        padding-left: 10px;
        padding-right:10px;
        text-align: center;
        font-size: 20px;
    }
</style>
<body>
    <div class="container">
        <h1>AREA OF A TRIANGLE</h1>
        <form method="POST">
            {% csrf_token %}
            <div class="calculate"> 
                Base:<input type="text" name="base" value={{b}}></input><br/>
            </div>
            <div class="calculate">
                Height:<input type="text" name="height" value={{h}}></input><br/>
            </div>
            <div class="calculate">
                <input type="submit" value="Calculatearea"></input><br/>
            </div>
            <div class="calculate">
                Area:<input type="text" name="area" value={{area}}></input>
            </div>
        </form>
    </div>
    
</body>
</html>
```
### view.py:
```
from django.shortcuts import render

def areacalculation(request):
    context ={}
    context["area"]='0'
    context["b"]='0'
    context["h"]='0'
    if request.method == 'POST':
        
        b=request.POST.get('base','0')
        h=request.POST.get('height','0')
        area=0.5*int(b)*int(h)
        context['area'] = area
        context['b']=b
        context['h']=h
    return render(request,"mathapp/area.html",context)
```
### urls.py:
```
from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('areaoftriangle/',views.areacalculation,name="areaoftriangle"),
    path('',views.areacalculation,name="areaoftriangleroot")
]
```

## OUTPUT:
![OUTPUT](https://user-images.githubusercontent.com/93427278/154802117-94bc1306-8b92-4f52-a0f8-697a7e632296.png)

## Result:
The code to execute mathematical website in server side has been created successfully
