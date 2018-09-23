+++
title = "Overview"

date = 2017-12-24
lastmod = 2018-03-02
draft = false

toc = true  # Show table of contents? true/false
type = "docs"  # Do not modify.

[menu.docs]
    parent = "deploy"
    identifier = "deployment"
    weight = 1
+++

Sites built using Academic can be deployed in a large variety of ways due to the static nature of the generated website. The recommended deployment method alongside a few of the other most popular techniques are described below.

If using Netlify, your site will be built automatically, otherwise run the `hugo` command in your terminal to generate your site in the `public/` folder - now it is ready to copy across to your host.

## Netlify

We recommend deploying your site with Netlify. Netlify is free and provides fast global access, automated deployment when you add or modify content, and one-click HTTPS security. [Check out our guide to deploy with Netlify]({{< relref "install.md#install-with-web-browser" >}}).

## GitHub Pages

Go to [Github](http://www.github.com/) and register for an account if you have not done so already. Github encourage using your real name as your username, and this can help your Github URL (which you will be assigned later) to have a professional appearance.

[Install Git](https://help.github.com/articles/set-up-git/) if it's not already present on your system. You can check by running `git --version` in your Command Prompt/Terminal app.

Once you have created your Github account and setup Git on your computer, we will create two new repositories (often abbreviated as *repos*) on Github with the following names:
                                                                    
- `academic-kickstart` or any other name you like - we will save your **content** to this repo
- `<USERNAME>.github.io` where `<USERNAME>` is your Github username - we will save the **generated website** to this repo

To create the `<USERNAME>.github.io` repository, click the "+" icon in the top right corner and then choose “New Repository”.
 
To create the `academic-kickstart` repository, [**fork**](https://github.com/sourcethemes/academic-kickstart#fork-destination-box) the *Academic Kickstart* repository and clone your fork with Git (download it to your computer) by replacing `<USERNAME>` in the following command with your Github username: 
                                         
    git clone https://github.com/<USERNAME>/academic-kickstart.git My_Website
    cd My_Website
    git submodule update --init --recursive
                                             
In your `config.toml` file, set `baseurl = "https://<USERNAME>.github.io/"`, where `<USERNAME>` is your Github username. Stop Hugo if it's running and delete the `public` directory if it exists (by typing `rm -r public/`).

Add your *<USERNAME>.github.io* repository into a submodule in a folder named *public*, replacing *<USERNAME>* with your Github username:

    git submodule add -f -b master https://github.com/<USERNAME>/<USERNAME>.github.io.git public

Add everything to your local git repository and push it up to your remote repository on GitHub:

    git add .
    git commit -m "Initial commit"
    git push -u origin master

Whilst running the above commands you may be prompted for your Github username and password.

Next, **regenerate** your website's HTML code by running Hugo and uploading the *public* submodule to GitHub:

    hugo
    cd public
    git add .
    git commit -m "Build website"
    git push origin master
    cd ..

Once Git has finished uploading your site to Github, you can open your new `https://<USERNAME>.github.io` website in your browser, substituting *<USERNAME>* with your Github username.

### Custom domains

You can further personalize your website with your own domain name.

We can highly recommend [Namecheap](https://www.namecheap.com/?aff=105828) for **registering a domain**, as they provide great value for money whilst providing fast support. To find a good domain that is available, try a mix of your first and last names or initials, with either a `.com` or `.me` ending.

**For Netlify deployments**, once your domain is registered, navigate to the *Custom domains* section of the Netlify admin panel and then follow [their wizard](https://www.netlify.com/docs/custom-domains/#assigning-a-custom-domain) to assign your domain to your site.

**For Github deployments**, you'll need to login to your domain registrar to point your domain to Github, and create a `CNAME` file in the `static` folder of your website, so that Github knows your intentions. For more information, check out the [domains guide by Github](https://help.github.com/articles/setting-up-a-custom-domain-with-github-pages/).

Remember that after you have setup a custom domain, you will need to wait approximately 24-48 hours for the DNS to propagate and then you'll need to update `baseurl` in your `config.toml` to your new URL, regenerate your site (see above section), and redeploy.

### Automating deployment

If you are feeling more adventurous, you can consider automating deployment so that when a change, such as a new blog post, is pushed to your `academic-kickstart` repository, your website (`<USERNAME>.github.io` repository) is automatically re-built.

## Amazon S3

By uploading the contents of your `public` folder to [Amazon S3](https://aws.amazon.com/s3/), your site can be served with dynamic scaling to almost unlimited traffic. This approach has the benefit of being one of the cheapest and most reliable hosting options available as you only pay for what you use.

## Web host via FTP

Use an FTP client to upload the contents of your `public` folder to a web host. This may be especially convenient for academic students and staff who are provided with university web space. 
