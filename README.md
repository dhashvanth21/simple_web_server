# EX01 Developing a Simple Webserver

# Date:30.9.2024
# AIM:
To develop a simple webserver to serve html pages and display the configuration details of laptop.

# DESIGN STEPS:
## Step 1:
HTML content creation.

## Step 2:
Design of webserver workflow.

## Step 3:
Implementation using Python code.

## Step 4:
Serving the HTML pages.

## Step 5:
Testing the webserver.

# PROGRAM:
```
views.py
from http.server import BaseHTTPRequestHandler, HTTPServer
from importlib.resources import contents
from django.http import HttpResponse
from django.shortcuts import render

content='''<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>LAPTOP SPECIFICATIONS</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: rgba(190, 177, 157, 0.647);
          
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .specs-container {
            background-color: honeydew;
            padding: 20px;
            border-radius: 10px;
            box-shadow: rgb(177, 177, 107);
            width: 400px;
        }
        h1 {
            text-align: center;
            color:rgb(204, 22, 22);
        }
        table {
            width: 100%;
            border-collapse: collapse;
        }
        th, td {
            padding: 10px;
            text-align: left;
            border-bottom: 1px solid rgb(165, 158, 158);
        }
        th {
            background-color: #c3c5cb;
        }
    </style>
</head>
<body>
    <div class="specs-container">
        <h1 style="font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;">LAPTOP SPECIFICATIONS</h1>
        <table style="font-family: 'Times New Roman', Times, serif;">
            <tr>
                <th style="font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;">Specification</th>
                <th style="font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;">Details</th>
            </tr>
            <tr>
                <td style="font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;">Brand</td>
                <td>LENOVO</td>
            </tr>
            <tr>
                <td style="font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;">Model</td>
                <td>ThinkPad E16 Gen 1</td>
            </tr>
            <tr>
                <td style="font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;">Processor</td>
                <td>13th Gen Intel(R) Core(TM) i5-1335U   1.30 GHz</td>
            </tr>
            <tr>
                <td style="font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;">RAM</td>
                <td>16 GB (15.7 GB usable)</td>
            </tr>
            <tr>
                <td style="font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;">Storage</td>
                <td>350.8 GB</td>
            </tr>
            <tr>
                <td style="font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;">Graphics</td>
                <td>NVIDIA GeForce GTX 1650</td>
            </tr>
            <tr>
                <td style="font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;">Display</td>
                <td>16inch Full HD</td>
            </tr>
            <tr>
                <td style="font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;">Battery Life</td>
                <td>Up to 48 hours</td>
            </tr>
            <tr>
                <td style="font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;">Operating System</td>
                <td>Windows 11</td>
            </tr>
            <tr>
                <td style="font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;">Price</td>
                <td>69000 INR</td>
            </tr>
        </table>
    </div>
</body>
</html>'''

class Myserver(BaseHTTPRequestHandler):
    def do_GET(self):
        print("Get request received...")
        self.send_response(200)
        self.send_header("content-type","text/html")
        self.end_headers()
        self.wfile.write(content.encode())
print("This is my webserver")
server_address =('',8000)
Httpd = HTTPServer(server_address,Myserver)
Httpd.serve_forever()

urls.py
from tempfile import template
from django.contrib import admin
from django.urls import path
from myapp1.views import Myserver

urlpatterns = [
    path('admin/', admin.site.urls),
    path('server/',Myserver.as_view())
]
```
# OUTPUT:
![Screenshot 2024-12-06 231547](https://github.com/user-attachments/assets/c2146eef-67b7-449e-872b-10fa9e7eca13)

![Screenshot 2024-12-07 110716](https://github.com/user-attachments/assets/316682ff-1e76-4d04-b7b8-86e5fb37b0eb)


# RESULT:
The program for implementing simple webserver is executed successfully.
