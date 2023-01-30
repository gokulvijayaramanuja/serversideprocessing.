# Design a Website for Server Side Processing

## AIM:
To design a website to perform mathematical calculations in server side.

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App.

### Step 4:
Create python programs for views and urls.

### Step 5:
Create a HTML of forms.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
```
math.html

<html>
<head>
<meta charset='utf-8'>
<meta http-equiv='X-UA-Compatible' content='Ie=edge'>
<title>Area of Rectangle</title>
<meta name='viewport' content='width=device-width, initial-sacle=1'>
<style>
body {
background-color:cyan;
}
.edge {
width: 1080px;
margin-left: auto;
margin-right: auto;
padding-top: 200px;
padding-left: 300px;
}
.box {
display:block;
border: Thick dashed lime;
width: 500px;
min-height: 300px;
font-size: 20px;
background-color:purple;
}
.formelt{
color:Red;
text-align: center;
margin-top: 5px;
margin-bottom: 5px;
}
h1{
color:yellow;
text-align: center;
padding-top: 20px;
}
</style>
</head>
<body>
<div class="edge">
<div class="box">
<h1>Area of a rectangle</h1>
<form method="POST">
{% csrf_token %}
<div class="formelt">
Length : <input type="text" name="length" value="{{1}}"></input>(in m)<br/>
</div>
<div class="formelt">
Breadth : <input type="text" name="breadth" value="{{b}}"></input>(in m)<br/>
</div>
<div class="formelt">
<input type="submit" value="Calculate"></input><br/>
</div>
<div class="formelt">
Area : <input type="text" name="area" value="{{area}}"></input>m<sup>2</sup><br/>
</div>
</form>
</div>
</div>
</body>
</html>

views.py

from django.shortcuts import render
def rectarea(request):
    context={}
    context['area'] = "0"
    context['l'] = "0"
    context['b'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        l = request.POST.get('length','0')
        b = request.POST.get('breadth','0')
        print('request=',request)
        print('Length=',l)
        print('Breadth=',b)
        area = int(l) * int(b)
        context['area'] = area
        context['l'] = l
        context['b'] = b
        print('Area=',area)
    return render(request,'myapp/math.html',context)

urls.py

from django.contrib import admin
from django.urls import path
from myapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('areaofrectangle/',views.rectarea,name="areaofrectangle"),
    path('',views.rectarea,name="areaofrectangleroot")
]
```
## OUTPUT:
![out (2)](https://user-images.githubusercontent.com/119577543/215425453-ccb0a669-fb2e-4e3f-b4c0-26275b6b7b45.png)

### Home Page:
![home1](https://user-images.githubusercontent.com/119577543/215425522-805060f9-8118-4626-a2b3-55d4587ec2b2.png)


## Result:
The program for implementing server side processing is completed successfully.
