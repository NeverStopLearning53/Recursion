# **Exercises**
# **Questions**

#### **1. Explain the difference between the request/response cycle.**
The Request/Response cycle is a method computers use to communicate with each other. One computer is requesting some data and the other computer is providing the data relating to the request. Is this the answer they were looking for or is it related to how this cycle is being implemented either asynchronomously or synchronomously.
#### **2. List common response codes and their groupings.**

* **200s** Ok/Success - The request was received and processed by the server successfully.
* **300s** Redirect - The request was
* **400s:** The reqestor made a mistake - The most common is "404: Not Found"
* **500s:** The server made a mistake - The server is down or some code on the server threw an error.
 received and then redirected somewhere else.

#### **3. Explain the common HTTP verbs: GET, POST, PATCH, PUT, and DELETE.**

* **GET**
The most common verb. It is what is used to retrieve a page from a server. This is what occurs by default when you put a URL into the browser or click on a link.
* **POST**
This is used to create a nw object on the server.
* **PATCH**
This is used to update an existing object on the server.
* **PUT**
This is used to replace an existing object on the server. It technically should only be used when sending a complete replacement for an object.
* **DELETE**
This is used to delete and object from the server.

#### **4. Explain the difference between synchronous and asynchronous code.**
When you execute something synchornously, you wait for it to finish before moving on to another task. When you execute something asychronously, you can move on to another task before it finishes. Most code run synchronously.
#### **5. Explain what a JavaScript promise is.**
Every time you make an asynchronous request, you will get back a promise. A promise is an object that wraps an asynchronous operation and notifies when it's done.
#### **6. Explain why CORS exists and how we can work around it.**
CORS stands for Cross-origin resource sharing. This is a mechanism that allows resources on one web page to be requested from a site outside the domain of the original webpage. If all CORS were allowed , your browser could be told by some malicious JavaScript to go download viruses and other bad things. To prevent that, all modern browsers disallow CORS by default. To work within the CORS restrictions, the requests we use will go through a proxy site. The site, `https://cors-anywhere.herokuapp.com/` will call out to our requested site, grab the data, not change it a bit, and return it back to us as it we had directly hit that site.
#### **7. Create a fetch request in JavaScript.**
```
let url = 'http://newsapi.org/v2/top-headlines?sources=hacker-news&apiKey=3b32d35e489d47fea03f52a928f034ed';
    
fetch(url) 
// Call the fetch function passing the url of the API as a parameter
.then(function() {
    // Your code for handling the data you get from the API
})
.catch(function() {
    // This is where you run code if the server returns any errors
});
```

### **8. It is time to build HackerNews from scratch! But you need easy access to an API for a list of all the stories currently there.**
1. Go to News API and click 'Get API Key' sign up for a free API key. 
2. Use your API key to create a fetch using this URL: `https://newsapi.org/v2/top-headlines?sources=hacker-news&apiKey=<YOUR_API_KEY_HERE>` 
3. Loop through the result data, and for each story on HackerNews, create an `<li>` tag that contains the contents of the story.**

```
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>Michael's Hacker News</title>
</head>
<body>
    <h1>Michael's Hacker News</h1>
    <script>
    
    let url = 'https://newsapi.org/v2/top-headlines?sources=hacker-news&apiKey=3b32d35e489d47fea03f52a928f034ed';

    fetch(url)
        .then(r => {
        return r.json();
        })
    .then(data => {
        let articles = data.articles; // get the array of results from the data object
        let articleList = document.createElement("ol"); //create a new <ol>
        let body = document.querySelector("body"); // attach to the <body> node of the DOM
        body.appendChild(articleList); // append the List to the body
        articles.map(article => {

        let articleItem = document.createElement("li"); // create a article item /// name may not be correct .. ask for help
        articleItem.innerHTML = 
        '<a href="' + article.url + '">' + article.title + "  " + article.description + "</a>"; // name may not be correct ask for help 
        articleList.appendChild(articleItem); // append each <li> to the <ol>
        });


        console.log(articles);
    
        });


    </script>

</body>
</html>
```


