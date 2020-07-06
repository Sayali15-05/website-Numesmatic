# website-Numesmatic
Mycart/templates/index.html:
<!doctype html>
<html lang="en">
  <head>
    <script>window.location= "/shop"</script>

    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

    <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css" integrity="sha384-9aIt2nRpC12Uk9gS9baDl411NQApFmC26EwAOH8WgZl5MYYxFfc+NcPb1dKGj7Sk" crossorigin="anonymous">

    <title>Hello, world!</title>
  </head>
  <body>
    <main role="main"  >

      <!-- Main jumbotron for a primary marketing message or call to action -->
      <div class="jumbotron" style=" font-family:cursive ; " >
        <div class="container"
          <u><i><h3 class="display-3" style="color:crimson; ">Hello, world!</h3></i></u>
          <p><i style=" color: indigo;">"One of the Ethnic sense of art is collection".
                  It is the platform where you are not just buying or exchanging your collection
                   but realizing the worth of your efforts. Here you can increase your collection
                   or can take inspiration to start. There is no age bar to have a collection hobby from a
                   kid to a aged person. Here we especially brings you the collection of different country's currencies and postal stamps.</i></p>
                    <a class="btn btn-success btn-lg" href="/shop" role="button">Go to our Main Page</a>

        </div>
      </div>


    </main>
    <!-- Optional JavaScript -->
    <!-- jQuery first, then Popper.js, then Bootstrap JS -->
    <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js" integrity="sha384-DfXdz2htPH0lsSSs5nCTpuj/zy4C+OGpamoFVy38MVBnE+IbbVYUew+OrCXaRkfj" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js" integrity="sha384-Q6E9RHvbIyZFJoft+2mJbHaEWldlvI9IOYy5n3zV9zzTtmI3UksdQRVvoxMfooAo" crossorigin="anonymous"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/js/bootstrap.min.js" integrity="sha384-OgVRvuATP1z7JjHLkuOU7Xw704+h835Lr+6QL9UvYjZE3Ipu6Tp75j7Bh/kR0JKI" crossorigin="anonymous"></script>
  </body>
</html>

Settings.py:

INSTALLED_APPS = [
    'shop.apps.shopConfig',
    'blog',

TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': ['mycart/templates',],

MEDIA_URL='/media/'
STATIC_URL = '/static/'
MEDIA_ROOT =os.path.join(BASE_DIR, 'media')
SITE_ID= 1

Mycart/Urls.py:
from django.contrib import admin
from django.urls import path, include
from django.conf import settings
from django.conf.urls.static import static
from .import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('shop/', include('shop.urls')),
    path('blog/', include('blog.urls')),
    path('', views.index),
]+ static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)

Mycart/Views.py:
from django.shortcuts import render
from django.http import HttpResponse

def index(request):

    return render(request,'index.html')
    
    Shop app/templates folder/shop folder/about.html:
{% extends 'shop/basic.html' %}
{% block title %} About Us {% endblock %}
{% block body %}
{% load static %}
<main role="main"  >

  <!-- Main jumbotron for a primary marketing message or call to action -->
  <div class="jumbotron" style=" font-family:cursive ; " >
    <div class="container"
      <u><i><h3 class="display-3" style="color:crimson; ">Hello, world!</h3></i></u>
      <p><i style=" color: indigo;">"One of the Ethnic sense of art is collection".
              It is the platform where you are not just buying or exchanging your collection
               but realizing the worth of your efforts. Here you can increase your collection
               or can take inspiration to start. There is no age bar to have a collection hobby from a
               kid to a aged person. Here we especially brings you the collection of different country's currencies and postal stamps.</i></p>

    </div>
  </div>

  <div class="container" style=" font-family:cursive ; ">
    <!-- Example row of columns -->
    <i>
    <div class="col">
      <h2>Creators and Editors:-</h2>
      <div class="col-md-4 my-2">
        <h2>Vedika K. Mamidwar</h2>
        <p> (VJTI-B.Tech IT Engineering)</p>
      </div>
      <div class="col-md-4">
        <h2>Sayali </h2>
        <p> (VJTI-B.Tech Mechanical Engineering)</p>
      </div>
    </div>
    </i>
    <hr>
  </div> <!-- /container -->
</main>
{% endblock %}

Shop app/templates folder/shop folder/basic.html:
<!doctype html>
  <html lang="en">
  <head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

      <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css" integrity="sha384-9aIt2nRpC12Uk9gS9baDl411NQApFmC26EwAOH8WgZl5MYYxFfc+NcPb1dKGj7Sk" crossorigin="anonymous">

    <title>{% block title %} {% endblock %}</title>
    {% block head %} {% endblock %}
  </head>
  <style>{% block css %} {% endblock %}</style>

<body >
  {% block additional_styles %}  {% endblock %}
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
  <a class="navbar-brand" href="/shop">Numismatic</a>
  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
  </button>

  <div class="collapse navbar-collapse" id="navbarSupportedContent">
    <ul class="navbar-nav mr-auto">
      <li class="nav-item active">
        <a class="nav-link" href="/shop">Home <span class="sr-only">(current)</span></a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="/shop/about">About Us<span class="sr-only">(current)</span></a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="/shop/contact">Contact Us</a>
      </li>
    
        <li class="nav-item">
          <a class="nav-link" href="/shop/registration/login">Login</a>
        </li>
      <li class="nav-item">
        <a class="nav-link" href="/shop/favourites">Sell</a>
      </li>

    </ul>
    <form method='get' action="/shop/search/" class="form-inline my-2 my-lg-0">
      <input class="form-control mr-sm-2" type="search" placeholder="Search here" aria-label="Search" name="search" id="search">
      <button class="btn btn-outline-secondary my-2 my-sm-0" type="submit">Search</button>
    </form>
    <button type="button" class="btn btn-secondary mx-2" id="popcart" data-container="body" data-toggle="popover" data-placement="bottom" data-html="true" data-content="Your Quick Views">
       Views(<span id="cart">0</span>)
    </button>
  </div>
</nav>
  {% block body %} {% endblock %}
  <!-- Optional JavaScript -->
  <!-- jQuery first, then Popper.js, then Bootstrap JS -->
  <script src="https://code.jquery.com/jquery-3.5.1.js" integrity="sha256-QWo7LDvxbWT2tbbQ97B53yJnYU3WhH/C8ycbRAkjPDc=" crossorigin="anonymous"></script>
  <script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js" integrity="sha384-Q6E9RHvbIyZFJoft+2mJbHaEWldlvI9IOYy5n3zV9zzTtmI3UksdQRVvoxMfooAo" crossorigin="anonymous"></script>
  <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/js/bootstrap.min.js" integrity="sha384-OgVRvuATP1z7JjHLkuOU7Xw704+h835Lr+6QL9UvYjZE3Ipu6Tp75j7Bh/kR0JKI" crossorigin="anonymous"></script>
  {% block js %}
  <script>

    if(localStorage.getItem('cart') ==null)
    {
      var cart={};
    }

    else
    {
      cart=JSON.parse(localStorage.getItem('cart'));
      document.getElementById('cart').innerHTML =Object.keys(cart).length;
    }

    $('.cart').click(function()
    {
      var idstr=this.id.toString();

      if (cart[idstr] !=undefined)
      {
        cart[idstr] = cart[idstr] + 1;
      }
      else
      {
        cart[idstr] = 1
      }
      localStorage.setItem('cart', JSON.stringify(cart));
      document.getElementById('cart').innerHTML =Object.keys(cart).length;

    });

    $('#popcart').popover('show');
    document.getElementById("popcart").setAttribute('data-content','<h5>Your Quick Views</h5>');


  </script>
  {% endblock %}

</body>
<footer>
  <div class="copyrights">

    <p> © 2020 All Rights Reserved | Designed by TeamGallantGirls</p>

  </div>
</footer>

</html>
Shop/models.py:
from django.db import models


class Product(models.Model):
    product_id= models.AutoField
    product_name= models.CharField(max_length= 50)
    description= models.CharField(max_length= 300,default="")
    category= models.CharField(max_length=50,default="")
    subcategory= models.CharField(max_length= 300,default="")
    price= models.IntegerField(default=0)
    publish_date= models.DateField()
    image=models.ImageField(upload_to="shop/images",default="")


    def __str__(self):
        return self.product_name

class Contact(models.Model):
    msg_id= models.AutoField
    name= models.CharField(max_length= 70)
    email= models.CharField(max_length= 100,default="")
    phone= models.IntegerField(default=0)
    desc= models.CharField(max_length=500,default="")

    def __str__(self):
        return self.name

class Login(models.Model):
    email= models.CharField(max_length= 100, default="")
    password= models.CharField(max_length=100, default="")

    def __str__(self):
        return self.email

shop/admin.py:
from django.contrib import admin
from .models import Product, Contact, Login

admin.site.register(Product)
admin.site.register(Contact)
admin.site.register(Login)

shop/urls.py:
from django.contrib import admin
from django.urls import path
from .import views

urlpatterns = [
    path("",views.index, name="shopHome"),
    path("about/",views.about, name="AboutUs"),
    path("contact/",views.contact, name="ContacUs"),
    path("search/",views.search, name=" search"),
    path("products/<int:myid>",views.prodView, name="prodView"),
    path("registration/login/",views.login, name="login"),
    path("sell/",views.sell, name="sell"),
]

shop/views.py:
from django.shortcuts import render
from django.http import HttpResponse
from .models import Product, Contact, Login, Order, OrderUpdate
from math import ceil
import json


def index(request):
    allProds=[]
    catprods=Product.objects.values('category', 'id')
    cats ={item['category'] for item in catprods}
    for cat in cats:
        prod= Product.objects.filter(category=cat)
        n=len(prod)
        nslides=n//4+ceil((n/4)-(n//4))
        allProds.append([prod, range(1, nslides), nslides ])

    params={ 'allProds':allProds}
    return render(request,'shop/index.html', params)

def about(request):
    return render(request,'shop/about.html')

def contact(request):
    if request.method=="POST":
        name = request.POST.get('name', '')
        email = request.POST.get('email', '')
        phone = request.POST.get('phone', '')
        desc = request.POST.get('desc', '')
        contact=Contact(name=name , email=email , phone=phone , desc=desc)
        contact.save()

    return render(request,'shop/contact.html')


def searchMatch(query, item):
    '''return true only if query matches the item'''
    if query in item.description.lower() or query in item.description.upper() or query in item.product_name.lower() or query in item.product_name.upper() or query in item.category.lower():
        return True
    else:
        return False

def search(request):
    query = request.GET.get('search')
    allProds=[]
    catprods=Product.objects.values('category', 'id')
    cats ={item['category'] for item in catprods}
    for cat in cats:
        prodtemp= Product.objects.filter(category=cat)

        prod=[item for item in prodtemp if searchMatch(query , item)]

        n=len(prod)
        nslides=n//4+ceil((n/4)-(n//4))
        if len(prod) !=0:
            allProds.append([prod, range(1, nslides), nslides ])
    params={ 'allProds':allProds, 'msg':""}

    if len(allProds) == 0 or len(query) < 4:
        params= {'msg':"Please make sure you entered relevant search query "}

    return render(request,'shop/search.html', params)

def prodView(request, myid):
    #Fetching product using id
    product= Product.objects.filter(id= myid)
    return render(request,'shop/prodView.html', {'product':product[0]})


def login(request):
    email = request.POST.get('email', '')
    password = request.POST.get('password', '')
    try:
        login= Login.objects.filter(email=email, password=password)
        if login==True:
            return render(request,'shop/registration/useraccount.html')
        else:
            return render(request,'shop/registration/login.html')
    except Exception as e:
        return HttpResponse('Please make sure you have entered correct email and password')

    return render(request,'shop/registration/login.html')


def sell(request):
    if request.method == 'GET':
        images_list = Product.objects.order_by('date')
        category= Product.objects.order_by('date')
    return render(request,'shop/sell.html')
    
    
    Shop app/templates folder/shop folder/search.html:
{% extends 'shop/basic.html' %}

{% block title %}Search Results {% endblock %}

{% block css %}

  .col-md-3
  {
    display:inline-block;
    margin-left:-4px;
  }

  .carousel-indicators .active{
      background-color:blue;
  }
  .carousel-container{
    background-color:black;
  }

  .col-md-3 img{
    height:125px;
    width:150px;
    margin:4px;
  }

  body .carousel-indicator li{
    background-color:blue;
  }

  body .carousel-indicators{
    bottom:0;
  }

  body .carousel-control-prev-icon,
  body .carousel-control-next-icon{
    background-color: blue;}

  .carousel-control-prev,
  .carousel-control-next{
    top:auto;
    bottom:auto;
  padding-top:145px;}

   body .no-padding{
     padding-left: 0;
     padding-right:0;
   }
{% endblock %}

{% block body %}
{% load static %}
<div class="container">

      <!-- Slideshow starts here -->
      {% for product,range, nslides in allProds %}
  <h4 class="my-4">{{product.0.category}}</h4>
  <div class="row">
<div id="demo{{forloop.counter}}" class="col carousel slide my-3" data-ride="carousel">
  <ul class="carousel-indicators">
    <li data-target="#demo{{forloop.counter}}" data-slide-to="0" class="active"></li>

    {% for i in range %}

    <li data-target="#demo{{forloop.parentloop.counter}}" data-slide-to="{{i}}" ></li>

    {% endfor %}
  </ul>

    <!-- Slideshow starts here -->
<div class="container carousel-inner no-padding">

  <div class="carousel-item active">


      {% for i in product %}
     <div class="col-xs-3 col-sm-3 col-md-3">
       <div class="card align-items-center" style="width: 18rem; height:19rem;">
         <img src='/media/{{i.image}}' class="card-img-top" alt="...">
          <div class="card-body">
            <h5 class="card-title"><h5>Rs.{{i.price}}</h5></h5>
            <p class="card-text">{{i.description|slice:"0:30"}}...</p>
            <a href="/shop/products/{{i.id}}"><button id="qv{{i.id}}" class="mx-2 btn btn-primary cart" >Quick View</button></a>{{i.publish_date}}
        <!--   <h6 class="date" style="  margin-left:130px;"> {{i.publish_date}}</h6>-->
          </div>
        </div>
     </div>

     {% if forloop.counter|divisibleby:4 and forloop.counter > 0 and not forloop.last %}
   </div><div class="carousel-item">
     {% endif %}

     {% endfor %}
         </div>

</div>

</div>

     <!-- left and right controls for slide -->
   <a class="carousel-control-prev" href="#demo{{forloop.counter}}" data-slide="prev">
     <span class="carousel-control-prev-icon"></span>
   </a>
   <a class="carousel-control-next" href="#demo{{forloop.counter}}" data-slide="next">
     <span class="carousel-control-next-icon"></span>
   </a>
  </div>

   {% endfor %}
  </div>

{% endblock %}

{% block js %}

<script>

  {% if msg|length != 0 %}
    alert(('{{msg}}'));
    window.location.href = "/"

  {% endif %}



  if(localStorage.getItem('cart') ==null){
    var cart={};

  }
  else{
    cart=JSON.parse(localStorage.getItem('cart'));
    document.getElementById('cart').innerHTML =Object.keys(cart).length;
  }

  $('.cart').click(function(){
    var idstr=this.id.toString();

    if (cart[idstr] !=undefined){
      cart[idstr] = cart[idstr] + 1;
    }

    else{
      cart[idstr] = 1
    }
    localStorage.setItem('cart', JSON.stringify(cart));
    document.getElementById('cart').innerHTML =Object.keys(cart).length;
  });
  $('#popcart').popover('show');
  document.getElementById("popcart").setAttribute('data-content','<h5>cart</h5>');

</script>

{% endblock %}
Shop app/templates folder/shop folder/search.html:
{% extends 'shop/basic.html' %}

{% block title %}Search Results {% endblock %}

{% block css %}

  .col-md-3
  {
    display:inline-block;
    margin-left:-4px;
  }

  .carousel-indicators .active{
      background-color:blue;
  }
  .carousel-container{
    background-color:black;
  }

  .col-md-3 img{
    height:125px;
    width:150px;
    margin:4px;
  }

  body .carousel-indicator li{
    background-color:blue;
  }

  body .carousel-indicators{
    bottom:0;
  }

  body .carousel-control-prev-icon,
  body .carousel-control-next-icon{
    background-color: blue;}

  .carousel-control-prev,
  .carousel-control-next{
    top:auto;
    bottom:auto;
  padding-top:145px;}

   body .no-padding{
     padding-left: 0;
     padding-right:0;
   }
{% endblock %}

{% block body %}
{% load static %}
<div class="container">

      <!-- Slideshow starts here -->
      {% for product,range, nslides in allProds %}
  <h4 class="my-4">{{product.0.category}}</h4>
  <div class="row">
<div id="demo{{forloop.counter}}" class="col carousel slide my-3" data-ride="carousel">
  <ul class="carousel-indicators">
    <li data-target="#demo{{forloop.counter}}" data-slide-to="0" class="active"></li>

    {% for i in range %}

    <li data-target="#demo{{forloop.parentloop.counter}}" data-slide-to="{{i}}" ></li>

    {% endfor %}
  </ul>

    <!-- Slideshow starts here -->
<div class="container carousel-inner no-padding">

  <div class="carousel-item active">


      {% for i in product %}
     <div class="col-xs-3 col-sm-3 col-md-3">
       <div class="card align-items-center" style="width: 18rem; height:19rem;">
         <img src='/media/{{i.image}}' class="card-img-top" alt="...">
          <div class="card-body">
            <h5 class="card-title"><h5>Rs.{{i.price}}</h5></h5>
            <p class="card-text">{{i.description|slice:"0:30"}}...</p>
            <a href="/shop/products/{{i.id}}"><button id="qv{{i.id}}" class="mx-2 btn btn-primary cart" >Quick View</button></a>{{i.publish_date}}
        <!--   <h6 class="date" style="  margin-left:130px;"> {{i.publish_date}}</h6>-->
          </div>
        </div>
     </div>

     {% if forloop.counter|divisibleby:4 and forloop.counter > 0 and not forloop.last %}
   </div><div class="carousel-item">
     {% endif %}

     {% endfor %}
         </div>

</div>

</div>

     <!-- left and right controls for slide -->
   <a class="carousel-control-prev" href="#demo{{forloop.counter}}" data-slide="prev">
     <span class="carousel-control-prev-icon"></span>
   </a>
   <a class="carousel-control-next" href="#demo{{forloop.counter}}" data-slide="next">
     <span class="carousel-control-next-icon"></span>
   </a>
  </div>

   {% endfor %}
  </div>

{% endblock %}

{% block js %}

<script>

  {% if msg|length != 0 %}
    alert(('{{msg}}'));
    window.location.href = "/"

  {% endif %}



  if(localStorage.getItem('cart') ==null){
    var cart={};

  }
  else{
    cart=JSON.parse(localStorage.getItem('cart'));
    document.getElementById('cart').innerHTML =Object.keys(cart).length;
  }

  $('.cart').click(function(){
    var idstr=this.id.toString();

    if (cart[idstr] !=undefined){
      cart[idstr] = cart[idstr] + 1;
    }

    else{
      cart[idstr] = 1
    }
    localStorage.setItem('cart', JSON.stringify(cart));
    document.getElementById('cart').innerHTML =Object.keys(cart).length;
  });
  $('#popcart').popover('show');
  document.getElementById("popcart").setAttribute('data-content','<h5>cart</h5>');

</script>

{% endblock %}



<html lang="en" dir="ltr">
  <head>
    <meta charset="utf-8">
    <title>Login</title>
      <link rel="stylesheet" type="text/css" href="style.css">
  <body>
    <div class="loginbox">
      <h1>Login here</h1>
      <form class="" action="index.html" method="post">
        <p>Username</p>
        <input type="text" name="" placeholder="Entre Username">
        <p>Password</p>
        <input type="password" name="" placeholder="Entre Password"><br>
        <input type="submit" name="" value="Login"><br>
        <a href="#">Forgot Password</a><br><br>
        <a href="#">Reset Password</a><br>
      </form>

    </div>
  </body>
  </<head>
</html>


*{
  margin: 0;
  padding: 0;
  background-size: cover;
  background-position: centre;
  font-family: sans-serif;
}

.loginbox{
  width: 320px;
  height: 420px;
  background: #f7e7ce;
  colour: #fff;
  top: 50%;
  left: 50%;
  position: absolute;
  transform: translate(-50%, -50%)
  box-sizing: border-box;
  padding: 70px 30px;
}

.h1{
  margin: 0;
  padding: 0 0 20px;
  text-align: centre;
  font-size: 22px;
  colour: #fff;
}

.loginbox p{
  margin: 0;
  padding: 0;
  font-width: bold;
}

.loginbox input{
  width: 200px;
  margin-bottom: 20px;
}

.loginbox input[type="text"] input[type="password"]
{
  border: none;
  border-bottom: 1px;
  background: transparent;
  outline: none;
  height: 40px;
  colour: #fff;
  fontsize: 16px;
}

.loginbox input[type="submit"]
{
  border: none;
  outline: none;
  height: 40px;
  background: #de3163;
  colour: #fff;
  text-align: centre;
  box-align: centre;
  position: centre;
  font-size: 18px;
  border-radius: 20px;
}

.loginbox input[type="submit"]:hover
{
  cursor: pointer;
  background: #ffc107;
  colour: blue;
}
.loginbox a
{
  text-decoration: none;
  font-size: 15px;
  line-height: 20px;
  color: Black;
}
.loginbox a:hover
{
  color: #ffc107;
}



<html>
<head>
  <title align=top>Registration</title>
  <link rel="stylesheet" type="text/css" href="register.css">
  </head>
    <body>
   <h1 align="centre>Registration</h1> </b>
      <div class="register">
        <form method="post" id="register" action="index.html">
          <h2>Resister</h2>
          <label for="Name :"></label><br>
            <input type="text" name="Name" id="name"
          placeholder="Enter your name"> <br>
          <label for="Mobile no :"></label><br>
          <select id="ph">
          </select>
            <input type="number" name="Mnum" id="num"
          placeholder="Enter your mobile number"><br><br>
          <label for="Email id :"></label>
            <input type="email" name="email" id="email"
          placeholder="Enter your email"><br>
          <label for="Address :"></label><br>
            <input type="text" name="address" id="address"
          placeholder="Enter your address"><br>
          <label for="Password :"></label><br>
            <input type="password" name="password" id="password"
          placeholder="Enter your Password"><br>
          <label for="Re Enter Password :"></label><br>
            <input type="password" name="password" id="password"
          placeholder=*{
   margin: 0;
   padding: 0;
   width: 200px;
   height: 25px;
   border: none;
   background: #ccccff;
   background-position: center;
   text-align: centre;
   box-sizing: border-box;
}

.reigister
{
  margin: 0;
  padding: 0;
  text-align: center;
  position: absolute;
}
.h2
{
  text-align: center;
  color: #be4585;
  position: absolute;
}
.reigister input[type=text],input[type=number],input[type=text],input[type=email],input[type=password]
{
  width: 100%;
  box-sizing: border-box;
  padding: 0;
  background: rgba(0, 0, 0, 0.5);
  outline: inherit;
  border: none;
  border-bottom: 2px #fff;
  color: #ffd700;
  border-radius: 5px;
  margin: 5px;
  font-weight: bold;
}
input[type=submit]
{
  width: 100%;
  box-sizing: border-box;
  padding: 10px 0;
  margin-top: 40px;
  outline: none;
  border-radius: 10px;
  text-align: center;
  border: none;
  background: #60adde;
  font-size: 20px;"Re-enter your pasword"><br><br>
          <input type="submit" value="Submit" id="sub">
        </form>
   </body>
</html>  















