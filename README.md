# Ex.05 Design a Website for Server Side Processing
# Date27/11/2025
# AIM:
To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side.

# FORMULA:
P = I2R
P --> Power (in watts)
 I --> Intensity
 R --> Resistance

# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Create python programs for views and urls to perform server side processing.

## Step 5:
Create a HTML file to implement form based input and output.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
```
math.html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lamp Power Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            margin: 0;
            padding: 0;
            text-align: center;
        }
        header {
            background-color: #4CAF50;
            color: white;
            padding: 20px;
            font-size: 24px;
        }
        main {
            margin: 20px auto;
            max-width: 500px;
            padding: 20px;
            background: white;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            border-radius: 8px;
        }
        label {
            display: block;
            margin-bottom: 5px;
            font-size: 18px;
            text-align: left;
        }
        input {
            width: 100%;
            padding: 10px;
            margin-bottom: 15px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 16px;
        }
        button {
            width: 48%;
            padding: 10px;
            margin: 5px 1%;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 4px;
            font-size: 16px;
            cursor: pointer;
        }
        button:hover {
            background-color: #45a049;
        }
        .result {
            margin-top: 20px;
            font-size: 20px;
            color: #333;
        }
        .error {
            color: red;
        }
    </style>
</head>
<body>
    <header>Lamp Power Calculator</header>
    <main>
        <label for="intensity">Intensity (I in Amperes):</label>
        <input type="number" id="intensity" placeholder="Enter intensity in amperes">
        
        <label for="resistance">Resistance (R in Ohms):</label>
        <input type="number" id="resistance" placeholder="Enter resistance in ohms">
        
        <button onclick="calculatePower()">Calculate Power</button>
        <button onclick="resetFields()">Clear Fields</button>
        
        <div id="result" class="result"></div>
    </main>
    <script>
        function calculatePower() {
            // Get user inputs
            const intensity = parseFloat(document.getElementById('intensity').value);
            const resistance = parseFloat(document.getElementById('resistance').value);
            const resultDiv = document.getElementById('result');

            // Validate inputs
            if (isNaN(intensity) || isNaN(resistance) || intensity <= 0 || resistance <= 0) {
                resultDiv.textContent = 'Error: Please enter valid positive numeric values for intensity and resistance.';
                resultDiv.className = 'result error';
                return;
            }

            // Perform calculation (P = I^2 * R)
            const power = Math.pow(intensity, 2) * resistance;

            // Display the result
            resultDiv.textContent = `The calculated power is: ${power.toFixed(2)} W`;
            resultDiv.className = 'result';
        }

        function resetFields() {
            // Clear input fields and result
            document.getElementById('intensity').value = '';
            document.getElementById('resistance').value = '';
            document.getElementById('result').textContent = '';
        }
    </script>
</body>
</html>

views.py

from django.shortcuts import render 
def lampspower(request): 
    context={} 
    context['power'] = "0" 
    context['i'] = "0" 
    context['r'] = "0" 
    if request.method == 'POST': 
        print("POST method is used")
        i = request.POST.get('I','0')
        r = request.POST.get('R','0')
        print('request=',request) 
        print('Intensity=',i) 
        print('Resistance=',r) 
        power = (int(i)*int(i))*int(r) 
        context['power'] = power 
        context['i'] = i
        context['r'] = r 
        print('Power=',power) 
    return render(request,'mathapp/math.html',context)

urls.py

from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('lampspower/',views.lampspower,name="lampspower"),
    path('',views.lampspower,name="lampspower")
]


```
# SERVER SIDE PROCESSING:
![alt text](<server side processing.jpg>)

# HOMEPAGE:
![alt text](<Screenshot 2025-12-20 203916.png>)

# RESULT:
The program for performing server side processing is completed successfully.
