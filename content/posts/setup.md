+++
title = 'How to Setup Your Personal Blog Using Github Pages'
date = 2024-04-22T14:48:19+08:00
draft = false
math = true
+++
## Introduction
The main objective of this blog is to show you how to build a personal blog using **[Github Pages](https://docs.github.com/en/pages)**. 

The first thing you may ask is why using these tools instead of using some other more famous tools like **[WIX](https://www.wix.com/)** or simply publishing on platforms like **[Medium](https://medium.com/)**? The reason is that using Github Pages gives you more control on the content and format of your website. And most importantly you can use it for free! Meaning you do not need to pay any money to build and publish your website. The website you built will be hosted on GitHub's github.io domain or your own custom domain.

As the saying there is no free lunch/dinner, we do sacrifice something for a free website. One cost is that it does take some time to learn how to build a website with these tools. Another cost is that we are only allowed to build static websites to be hosted on Github Pages. To be specific, a static website, comparing to a dynamic website, is made of fixed code. Meaning only the site developer, which will be yourself, can make changes to the website. There will be no interactions between a website visitor and the website. For example, users are not able to leave comments or click on like/dislike buttons. 

For the first limitation, there are some tools can help to flatten the learning curve. And **[Hugo](https://gohugo.io/)** is one of the tools we are going to use. For the second limitation, although there is no solution to it, it still makes a lot of sense to use Github Pages host your personal resume or blog writings. So if you are interested to build a free personal website, I will show you in this blog to guide you through the process of setting up everything.

## Tools to be used
The main tool will be used to build the website is **[Hugo](https://gohugo.io/)**, which is *one of the most popular open-source static site generators* according to its website. To install Hugo, just refer to the instructions on its doc page https://gohugo.io/installation/.

Of course to use Github Pages you need to have a Github account. Visit https://github.com/ and follow the steps there to sign up your account.

That's it, now we are ready to start building our personal websites!

## Step 1: Create the site
Run the following code in your terminal line by line, it will help you create your website with the name *[your-github-username].github.io*. If you do not know how to find your github username, just log into your github account and click on the avatar on the top-right corner. The name showing right besides your avatar is your github username. 
```bash {class="my-class" id="create-site" lineNos=inline tabWidth=2}
hugo new site [your-github-username].github.io
```

After creating your site, there should be a folder with the name *[your-github-username].github.io* under your current directory. Use the following command to change to that directory.
```bash {class="my-class" id="cd-folder" lineNos=inline tabWidth=2}
cd [your-github-username].github.io
```

In the *[your-github-username].github.io* directory, run the following codes line by line. The codes help you add a theme to your website. Here I am using a theme called [Paper](https://themes.gohugo.io/themes/hugo-paper/). You are feel free to use any other themes. A good place to find themes is Hugo's [theme](https://themes.gohugo.io/) website. 
```bash {class="my-class" id="add-theme" lineNos=inline tabWidth=2}
git init
git submodule add https://github.com/nanxiaobei/hugo-paper themes/paper
echo "theme = 'paper'" >> hugo.toml
```
A more in-depth explanation of the above code, the first row is to create an empty Git repository. Which includes all the necessary subdirectories and files. The second line is to add the theme as a file under the Hugo themes folder. In the example above I used the theme from https://github.com/nanxiaobei/hugo-paper and added into theme directory with name *paper*. The last line is just to use the added *paper* theme by adding it into the hugo.toml file, which is the file holding all configurations for your site. You can also modify the **title** field in the hugo.toml file to change the name of your website.
```bash {class="my-class" id="launch-site" lineNos=inline tabWidth=2}
hugo server
```
You will see some message ending with the following on your terminal.
```
Now you have your first site set up. To run it locally, you can run the following code in your terminal.

Web Server is available at http://localhost:1313/ (bind address 127.0.0.1) 
Press Ctrl+C to stop
```
Open the http://localhost:1313/ link on your web browser and you can see your first site.

## Step 2: Create a post
With the website created, it is time to add some content to it. With Hugo you can create your post using the following command.
```bash {class="my-class" id="create-post" lineNos=inline tabWidth=2}
hugo new content posts/[name-of-your-post].md
```
The above code will create a file under the directory content/posts. Noted that the format of your post is *md*, which is [Markdown](https://www.markdownguide.org/getting-started/) that typically be used to add formatting elements to plaintext texts. In the created [name-of-your-post].md you can edit the metadata of your post's content. In Hugo it has another name called *Front Matter*. The Front Matter is included between the +++ signs. The front matter I used when writing this blog is as follows:
```
+++
title = 'How to Setup Your Personal Blog Using Github Pages'
date = 2024-04-22T14:48:19+08:00
draft = true
math = true
+++
```

Following the front matter, you can add the content. To format your content, you can use the Markdown [cheatsheet](https://www.markdownguide.org/cheat-sheet/). Some basic syntax for markdown elements are:
1. \# H1, \#\# H2, \#\#\# H3 for headings
- # H1
- ## H2
- ### H3
2. \*\*bold text\*\* for **bold text**.
3. \*italicized text\* for *italicized text*.
4. \[text](https://www.example.com) for [text](https://www.example.com) with hyperlink redirect to the given URL.

Sometimes you may need to include images in your post. Firstly, save your image under the directory static/images/. 
![screenshot](/images/screenshot.png)
Next, use the following syntax in your content to display the image.
```
![cdma](/images/cdma.jpg)
```
![cdma](/images/cdma.jpg)


Another important feature I used a lot is math typesetting. This feature allows me to use $\LaTeX{}$ syntax to write mathematical equations. To use this feature, you need to first ensure the Hugo template you used actually supports [MathJax](https://www.mathjax.org/) or [KaTeX](https://katex.org/). As we are using the theme from https://github.com/nanxiaobei/hugo-paper, the theme supports KaTex and we can simply set `math = true` in the front matter. Then we can use $\LaTeX{}$ syntax to write equations conveniently. For example by adding
```
$$x = \frac{-b \pm \sqrt{b^2-4ac}}{2a}$$
```
in the content, we can get 
$$x = \frac{-b \pm \sqrt{b^2-4ac}}{2a}$$

Now we are ready to deploy our first post on Github Pages and make it accessible to others!

## Step 3: Deploy the site
To deploy your site, you need to first create a Github repo with the same name as your Hugo project *[your-github-username].github.io*. Refer to this [link](https://docs.github.com/en/repositories/creating-and-managing-repositories/quickstart-for-repositories) if you do not know how to create your repo on Github.

Next, connect your local repo, which is the *[your-github-username].github.io* project folder on your local, to the Github repo. On how to link your local repo to the one created on Github, you can refer to the instructions [here](https://docs.github.com/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/adding-locally-hosted-code-to-github#adding-a-local-repository-to-github-using-git). 

Once you successfully connect your local repo to Github, there are a few more steps before committing your local changes. Do you remember in the *Front Matter* part of your content there is a field called **draft** and its value is set to true? 
```
+++
title = 'How to Setup Your Personal Blog Using Github Pages'
date = 2024-04-22T14:48:19+08:00
draft = true
math = true
+++
```
That draft variable means everything you added to the content is just a draft and will not be published to your website. Let us change the value to false now. After that, we can run the following command in your terminal
```bash {class="my-class" id="publish" lineNos=inline tabWidth=2}
hugo
```
It will publish all your changes into the **public** folder and now we are ready to commit to Github.

After running git add, git commit and git push. Your changes will be on github repo. But we are still missing one important final step to see your website. Since we are using Hugo to build the website, we need to let Github know how to set up Hugo on the server side. To achieve that, we can use a thing called **workflow** on Github to automate the process. Firsly, follow the steps in the image below to setup the Github Pages in your github repo.
![workflow](/images/workflow.png)
Secondly, go the Actions and click on New workflow.
![action](/images/action.png)
Name the workflow as **hugo.yaml** and replace the content of this file by **[this yaml file](/hugo.yaml)**. If your Github branch name is not *main* and your Hugo version is not 0.125.3, you should change in the hugo.yaml file accordingly before committing. Commit changes and wait for the changes to be deployed. 

After everything finished successfully, you will see your website through the link *[your-github-username].github.io*. 

And this is how to use Hugo and Github Pages to create your own website.

