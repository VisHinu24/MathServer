# Ex.05 Design a Website for Server Side Processing
## Date:02/05/2024

## AIM:
To design a website to find surface area of a Right Cylinder in server side.

## FORMULA:
Surface Area = 2Πrh + 2Πr<sup>2</sup>
<br>r --> Radius of Right Cylinder
<br>h --> Height of Right Cylinder

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
math.html
```
<!DOCTYPE html>
<html>
<head>
<meta charset='utf-8'>
<meta http-equiv='X-UA-Compatible' content='IE=edge'>
<title>Area of Surface</title>
<meta name='viewport' content='width=device-width, initial-scale=1'>
<style type="text/css">
body {
    background-color: lavender;
    font-family: Arial, sans-serif;
}

.edge {
    width: 100%;
    padding-top: 50px;
    text-align: center;
}

.box {
    display: inline-block;
    border: 2px solid rgb(123, 171, 239);
    width: 400px;
    min-height: 300px;
    font-size: 16px;
    background-color: rgb(231, 239, 116);
    padding: 20px;
    border-radius: 10px;
}

.cal {
    color: black;
    text-align: left;
    margin-bottom: 10px;
}

h1 {
    color: black;
    margin-top: 0;
}
</style>
</head>
<body>
<div class="edge">
    <div class="box">
        <h1>Surface area of Right Cylinder</h1>
        <h3>Vishinu H(212223220124)</h3>
        <form method="POST">
            {% csrf_token %}	
            <div class="cal">
                Radius: <input type="text" name="radius" value="">m<br/>
            </div>
            <div class="cal">
                Height: <input type="text" name="height" value="">m<br/>
            </div>
            <div class="cal">
                <input type="submit" value="Calculate"><br/>
            </div>
            <div class="cal">
                Area: <input type="text" name="area" value="{{area}}">m<sup>2</sup><br/>
            </div>
        </form>
    </div>
</div>
</body>
</html>


```
views.py
```
from django.shortcuts import render
def surfacearea(request):
    context = {}
    context['area'] = "0"
    context['r'] = "0"
    context['h'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        print('request.POST:', request.POST)
        r = request.POST.get('radius', '0') 
        h = request.POST.get('height', '0') 
        print('radius =', r)
        print('height =', h)
        area = 2 * 3.14 * int(r) * int(h) + 2*3.14*int(r)*int(r)
        context['area'] = area
        context['r'] = r
        context['h'] = h
        print('Area =', area)
    
    return render(request, 'mathapp/math.html',context)
```
urls.py
```
from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('surfacearea/',views.surfacearea,name="surfacearea"),
    path('',views.surfacearea,name="surfcaearea")
]

```
## SERVER SIDE PROCESSING:
![Screenshot 2024-05-02 112549](https://github.com/VisHinu24/MathServer/assets/144244396/30909652-1f9c-4578-b9db-56b7bcabd96e)


## HOMEPAGE:
![Screenshot 2024-05-02 112533](https://github.com/VisHinu24/MathServer/assets/144244396/e78b41fa-8a3f-4d1c-969e-9be5e066d32f)


## RESULT:
The program for performing server side processing is completed successfully.
