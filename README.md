# InstagramPostMaker

This project uses flask as a backend and BeatifulSoup Library of Python to web scrap a business news site and presents the headlines as a post that can be downloaded and posted in social media platforms.  

Made By: **Souradeep Kar**  
**Personal Project**  
Tech Stack:   
* Frontend technologies:-  
&emsp; **HTML**, **CSS**, **TailwindCSS** framework, **html2canvas**  for converting the html tag content to a visual downloadable post.  
&emsp; Refer to https://html2canvas.hertzen.com/ for more details.  
* Backend Technologies:-  
&emsp; **Flask** backend framework, **BeautifulSoup** python library for web scraping the data from website.  
  
## What does the project aim to do? ##  
  
Sites like [indiatimes.com](https://indiatimes.com), [timesofindia.com](https://timesofindia.com), [news18.com](https://news18.com) provide us with truckloads of news from all different domains and contexts. As an end user, if you wish to find news of one particular kind, you don't necessary need to get bombarded with all kinds of news stories. This project aims to do the same in the context of extracting the latest news in the information technology domain and present the headlines to the user in a very visually appealing way (in the form of a post) that can be downloaded and uploaded on social media platforms later on. Hence, the project has automated the work of fetching latest news from reliable website in real time and making an uploadable post out of it. 
  
For this I have chosen the site [businesstoday.in](https://www.businesstoday.in/technology/news) from where I will scrap the news headlines using BeautifulSoup library in Python. For example, the screen recording embedded below demonstrates the list of headlines present in that webpage.



https://user-images.githubusercontent.com/91742260/180193691-0762b9d7-9663-45c4-ae2c-4898d3749bd2.mp4  
  
And the screen recording embedded below demonstrates how those headlines are put into the form of an instagram post. Every time the window is reloaded, one image gets selected randomly out of the five images present in the [images](https://github.com/souradeep852/InstagramPostMaker/tree/main/static/images/) folder, as the background of the post. The images present in this folder have been made using [Canva](https://canva.com). The "Download Post" button then allows you to download and share it.

  
  


https://user-images.githubusercontent.com/91742260/180196669-385fbc30-edd2-458d-94ac-f1c462527a21.mp4
  
Here are a few examples of the posts generated:-

![technewspost](https://user-images.githubusercontent.com/91742260/180197465-4c514858-940b-48a3-b77b-b6e94c67d782.jpg)

![technewspost (2)](https://user-images.githubusercontent.com/91742260/180197820-c5789a74-42d6-44c9-8794-5a6b142fc1fe.jpg)


  
 ## How does it work? ##
 ### Requirements ###
 All the requirements for running the project have been specified in the [requirements.txt](requirements.txt) file using the command 
 ```
 pip freeze > requirements.txt 
 ```
 during the development process. Check whether the "requests" module is already present or not, by running ``` pip install requests```. 
 In order to run the application, the system must also have flask and beautifulsoup installed in it. These modules can be installed using the following commands:
 ```
 pip install flask
 pip install beautifulsoup
 ```
 First, let us analyze the code in [app.py](app.py). To get started, I just copy-pasted the boilerplate code present in the [Flask Documentation](https://flask.palletsprojects.com/en/2.1.x/quickstart/), as embedded below.
   
 ```
from flask import Flask, render_template
from requests

app= Flask(__name__)
@app.route('/', methods=["GET","POST"])
def index():
```

Inside the index() function lies the main code which does the job of web scrapping the site and gather the information. To use, that code we first need to install BeautifulSoup4 python library.
```
pip install beautifulsoup
```
and add import the module at the top of the app.py file using:
```
from bs4 import BeautifulSoup
```
Then comes the code for web scrapping. Following code snippet does the work for getting the 6 topmost headlines from the specified website, and return it in the form of a string in the above-mentioned index() function.
```
url="https://www.businesstoday.in/technology/news"
req=requests.get(url)
soup=BeautifulSoup(req.content, "html.parser")
finalnews=""
outerdata=soup.find_all("div", class_="widget-listing", limit=6)
for data in outerdata:
    news=data.div.div.a['title']
    finalnews+= "\u2022 " + news + '\n' + '\n'
return render_template("index.html", News=finalnews)
```
Using the inspect element feature of Chrome Dev tools, it was found out that all the news headlines fell under the div tag, having ```class="widget-listing"```. Hence, the  variable outerdata stores the contents of the div tags having ```class="widget-listing"``` and limiting upto a number of 6. Within this div tag, were two more nested div tags and one anchor tag. The headline itself was mentioned as the title of the anchor tag. Therefore we store the headline in the variable ```news``` at every iteration of the for loop and the variable contents are concatenated to the ```finalnews``` variable (with a bullet point at the start and two newlines at the end) which is finally returned out of the function, index(). ```render_template``` connects the backend of the app to its frontend file index.html, and passes the variable ```News```.
