# Ex.05 Design a Website for Server Side Processing
## Date:
18.04.2024
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
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        input{
            border-radius: 30px;
            text-align: center;
        }
        .box {
    display: inline-block;
    border:darkgray;
    width: 500px;
    min-height: 300px;
    font-size: 20px;
    background-color: palevioletred;
}
        body {
            background-color:lightpink;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;

        }
        
    </style>
</head>
<body name="body" id="body">
    <script>
        let number=['0','1','2','3','4','5','6','7','8','9','a','b','c','d','e','f'];
        function changeColor(){
            hexcode='';
            for(let i=0;i<6;i++){
                random1=Math.floor(Math.random()*number.length);
                hexcode+=number[random1];
            }
            hexcode="#"+hexcode;
            let b=document.getElementById('body');
            b.style.backgroundColor=hexcode;
        }
        setInterval('changeColor()',100);
        function check(){
            radius=document.getElementById('radius').value;
            height=document.getElementById('height').value;
            result=document.getElementById('result');
            area =  2*(3.14)radius*height + 2(3.14)*radius*radius;
            result.value = area;
        }
    </script>
    <div class="edge"></div>
    <div class="box">
    <center>
        <h1>Surface Area of Cylinder</h1>
        <b>RAMYA R (212223230169)<b>
        <h3>Radius : <input size="30px" type="text"  name="radius" id="radius" placeholder="Enter the Radius of the cylinder">m <br> <br>
        Height : <input type="text" size="30px" name="height" id="height" placeholder="Enter the Height of the cylinder">m <br><br>
        <button type="button" onclick="check()">AREA</button> <br> <br>
        Output : <input type="text" size="30px" name="result" id="result" placeholder="Output"> m<sup>2</sup></span></h2>
    </center>
</div>
</div>
</body>
</html>
```
```
Views.py
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
```
urls.py
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
![Screenshot 2024-04-18 112609](https://github.com/ramya23000505/MathServer/assets/149370791/1caefe7f-9054-4f52-be29-0234af0e3b81)
## HOMEPAGE:
![Screenshot 2024-04-18 112609](https://github.com/ramya23000505/MathServer/assets/149370791/9f89e6b1-1584-45e4-b06e-faec59d7b667)
## RESULT:
The program for performing server side processing is completed successfully.
