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
  
### What does the project aim to do? ###  
  
Sites like [indiatimes.com](https://indiatimes.com), [timesofindia.com](https://timesofindia.com), [news18.com](https://news18.com) provides us with truckloads of news from all different domains and contexts. As an end user, if you wish to find news of one particular kind, you don't necessary need to get bombarded with all kinds of news stories. This project aims to do the same in the context of extracting the latest news in the information technology domain and present the headlines to the user in a very visually appealing way (in the form of a post) that can be downloaded and uploaded on social media platforms later on.  
  
For this I have chosen the site [businesstoday.in](https://www.businesstoday.in/technology/news) from where I will scrap the news headlines using BeautifulSoup library in Python. For example, the screen recording embedded below demonstrates the list of headlines present in that webpage.



https://user-images.githubusercontent.com/91742260/180193691-0762b9d7-9663-45c4-ae2c-4898d3749bd2.mp4  
  
And the screen recording embedded below demonstrates how those headlines are put into the form of an instagram post. Every time the window is reloaded, one image gets selected randomly out of the five images present in the [images](https://github.com/souradeep852/InstagramPostMaker/static/images/) folder, as the background of the post. The images present in this folder have been made using [Canva](https://canva.com). The "Download Post" button then allows you to download and share it.

  
  


https://user-images.githubusercontent.com/91742260/180196669-385fbc30-edd2-458d-94ac-f1c462527a21.mp4
  
Here are a few examples of the posts generated:-

![technewspost](https://user-images.githubusercontent.com/91742260/180197465-4c514858-940b-48a3-b77b-b6e94c67d782.jpg)

![technewspost (2)](https://user-images.githubusercontent.com/91742260/180197820-c5789a74-42d6-44c9-8794-5a6b142fc1fe.jpg)


