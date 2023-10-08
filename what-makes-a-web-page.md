# What makes a web page?

Amost every web pages you see on the internet are made of three core building blocks, that is, HTML, CSS, and JavaScript. In this article, I will explain what these languages are, what roles they play in web development. 
Along with my explaination, I will use one of my project as an example to illustrate how the three languages work to create an interactive website. The project is a simple to-do list that allows the users to add their tasks to a list by enter task names in a input field and hit an add button. The entered task names will be add to a list. Every added task name has a check box and a bin symbol so that the users can either tick the checkbox when the task is done or delete it by clicking the bin symbol.

## HTML

**Hypertext Markup Language (HTML)** is a markup language that provides the content and structure of websites. If a website were a human body, then HTML would be used to build the skeleton. It structures a site or a document into elements, namely headings, paragraphs, sections, images, buttons, etc, and gives them basic formats. To see how a HTML document and the page it creates look like, let us dive into the example below. 

```
<!DOCTYPE html>
<html lang="en">

<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width" />
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.2/css/all.min.css">
<link rel="stylesheet" type="text/css" href="styles.css" />
</head>

<body>
    <div class="container">
        <h1 id="title">My To-do List</h1>
        <div id="newtask">
            <input id="addtask" type="text" placeholder="Enter your task">
            <button id="push">Add</button>
        </div>

        <div id="tasks"></div>
    </div>
</body>

</html>
```

![Alt text](https://drive.google.com/file/d/1AiqOlj45Ckgl8sfgzEpBJomCdaVNLmUn/view?usp=drive_link)

The page contains three visible elements, namely a title "My To-do List", an input field, and a button. To create this page, HTML labels the elements using HTML tags. Most of HTML elements has an opening tag `<>` and a closing tag `</>` with the content wrapped between these two tags. 

As seen in the example, the heading `<h1>` prints the content of the title, `<h1>  My To-do List </h1>`, and the `<button>` tags wrap around the content "Add". In the sample HTML document, we can also see three `<div>` tags, the Content Division Element. One wraps around `<h1>` and two other `<div>` tags, one of which encloses `<input/>` and `<button>` elements while the other appears to have no content at all. `div>` acts like a container for HTML contents. For instance, the empty `<div>` is actually a container for the future list of tasks to be done once the users enter some task names into the input field. If I removed all the `<div>` tags now, the result page would stay intact since they have no effect on either the content or the layout; however, we will see in the next section these `<div>` soon become relevant once the document is styled by CSS. 

Not all HTML elements have a separate closing tag. Some only have one single tag, which is called self-closing tag. One example is `<input/>` or simple `<input>` element that embeds an input field into a document to accept data from the user. 

To provide additional information to HTML elements, we can add attributes in their opening tags. For instance, the `<button>` element has the unique identifier `id` so that we can latter have access to this element in the CSS file to apply some styling to it. The `<input>` element has two attributes `type` and `placeholder`, which respectively set the type of input that this field accepts as text and define the text displayed in the input field when it has no value.

All of the elements we have discussed so far are somewhat visible on the web page; therefore, they are enclosed in `<body>`. There are three other important parts of a typical HTML document, namely `<!DOCTYPE>`, `<html>`, and `<head>`. Unlike `<body>`, these elements and their content are hidden from display. 

`<DOCTYPE>` declares the document type and it is strictly requires every HTML document starts with `<!DOCTYPE html>` while `<html>` represents the root element of an HTML document, which means that all other HTML elements must be at a lower level than `<html>`. The two direct descendants of `<html>` are `<head>` and `<body>`. `<head>` element contains metadata describing the HTML document. In the current example, the detailed description is as follow. 

1. `<meta charset="UTF-8" />`: In order for the displayed texts on websites being readable by users, the browser has to use some character encoding, which works like a dictionary, to translate machine code to human-readable text and vice versa. In this case, the `<meta>` specifies the browser is using the `utf-8` character encoding
2. `<meta name="viewport" content="width=device-width" />`: The viewport is the user's visible area of a web page. Since the viewport varies with the device, this `<meta>` sets the width of the viewport to the width of the device running the web page in order to make sure that the web page can work well in a large variation of screen sizes and orientations.
3. `<link rel="stylesheet" type="text/css" href="styles.css" />`: The `<link>` element links the CSS document, which is in charge of styling the web page, to the HTML document.
4. `<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500&display=swap">`: This `<link>` element provides a link to the Google Font web page from which the font style of the content is employed in the HTML document.  
5. `<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.2/css/all.min.css">`: This `<link>` element provides a link to the Cloudflare web page from which some special symbol is used in the HTML document. 
6. `<title>Todo List</title>`: The `<title>` defines the title of web page, which is shown in the website's tab or a broswer's title bar.  

## CSS

**Cascading Style Sheets (CSS)** is a design language that defines the appareance of the website. If HTML builds a skeleton, CSS provides the skin and hair. It dictates how the web page looks like at the end users. This is where we can pick the background color of the site, font-style of the text, adjust the font-size, containers' height and width, and so much more. CSS is a powerful tool for web developers since it is what sets the style and the mood of the web page, makes it more attractive and appealing to the users. In the screenshot below, we can see how the appearance of our To-do List web page has changed after CSS is added. 

![Alt text](https://drive.google.com/file/d/1dbI1NAPEM9jykuZppHYftEI8pia0Aj6r/view?usp=drive_link)

In the current example, a lot of styling has been done; the container of the heading, input field, and the button has been moved to the center of the page, the background color has changed to orange, the font-size, and color of texts has been under some adjustments, and so forth. In order to make these changes using CSS, we must first select the HTML elements we want to style, using CSS selectors. While there are various types of selectors, here we will discuss `id` selector. Technically, an `id` selector, which has the syntax as `#nameOfAttribute`, selects an HTML element that shares the same `id` attribute as the selector.  In the previous section, we have come across the `HTML` element `<button id="push">Add</button>`, which has `id="push"`. To select this button element in CSS, we can simply use a `#`, a hashtag character, followed by the button's `id` attribute, which gives us a CSS `id` selector `#push`. 

After selecting the element we want, the next step is to specify how we want the chosen element to look like. Every element has a range of attributes, each of which has their own set of values. The button in the example has `border` attribute whose value can determine whether the button is bordered or borderless, `color` whose values defines the color of the text printed on the button, `background-color` whose value sets the background color of the button, and so on. The way we change the appearance of the element we picked is by listing out attributes that we want to change and the value we want the attribute to change to. Below is the CSS code that adjusts the position, sets the shape, colors, and sizes of the button and the text inside it. The result can be seen in the previous image which shows the look of our To-do List after applying CSS.   

```
#push{
    position: relative;
    float: right;
    font-weight: 500;
    font-size: 16px;
    background-color: #cd6d06;
    border: none;
    color: #ffffff;
    cursor: pointer;
    outline: none;
    width: 20%;
    height: 45px;
    border-radius: 5px;
    font-family: 'Poppins',sans-serif;
}
```

While the To-do List is now better structured and looks more attractive, it is still far from being functional. Even though the user can type some task in the input field and click the 'add' button, the site does not store the task  into a list. Also, we still do not have a list which we can add more tasks to or delete some tasks from. In other to do all of that, we need to add interactivity to our website, using JavaScript. 

## JavaScript

**JavaScript** is a programming language that adds the interactivity to the website. To understand the role JavaScript plays in web development, let us continue with our analogy between human anatomy and a web page. Our body is programmed to take some action when some event happens. For instance, when it is cold, we wear more clothes, when we feel hungry, we eat or when someone greets us, we greet them back. Our website can also be programmed to react to events like our body. While our body is programmed by nature and education, websites are programmed by JavaScript code. If HTML builds the skeleton, CSS adds skin and hair to complete the appearance, JavaScript programms the brain that provides motions and behaviours of the muscles, and limbs. 

Just like the brain needs access to muscles to instruct their movements, JavaScript also needs access to HTML elements to program their responds to events. This can be done by using the `id` selector we learnt in the CSS section. In the current example, `document.querySelector('#push')` allows us to pick out the `<button>` element in the HTML `document` that has the `id` attribute value as "push", `document.querySelector('#addtask')` selects the input field `<input>` that has the `id` attribute value as "addtask", and `document.querySelector('#tasks')` picks out the division `<div>` which has the `id` attribute value as "tasks". This is the empty `<div>` we saw the HTML document in the first section, which accommodates tasks in the To-do List once the user adds them. 

Now we needs specify the events to which our website reacts in some way when they happens. `addEventListener()` is a function that instructs the site to look out for to some event and do something when the event takes place. In our example, `document.querySelector('#push').addEventListener('click', function(){...}` requests the site to do carry out a set of actions once the button is clicked. This set of action is specified in the following curly brackets `{...}`. Accordingly, once the user clicks the button, if the input field, is empty, then the site should send an alert message to the user, asking them to enter a task in the input field. If some task is already entered in the input field, then the task name together with a checkbox and a delete must be printed in the degsinated divsion that we select. If the user keeps adding more tasks, we will have a list of tasks as a result, each of which has a checkbox and an delete button. These delete buttons can be programmed so that the site can listen to the click event of these button and delete the tasks corresponding with them, using `addEventListener()` function. 

```
document.querySelector('#push').addEventListener('click', function(){
            if(document.querySelector('#addtask').value.length === 0){
                alert("Please Enter a Task")
            } else{
                document.querySelector('#tasks').innerHTML += `
                    <div class="task">
                        <button class="delete">
                            <i class="far fa-trash-alt"></i>
                        </button>
                        <div class="taskname">
                            ${document.querySelector('#newtask input').value}
                        </div>
                    </div>
                `;
                const currentTasks = document.querySelectorAll(".delete");
                for(let i=0; i<currentTasks.length; i++){
                    currentTasks[i].addEventListener('click', function(){
                        this.parentNode.remove();
                    }
                )}
            }
        })
```