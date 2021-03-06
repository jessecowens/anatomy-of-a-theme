# Anatomy Of A Theme

## Description

In this lesson you'll learn about the different files that make up a theme and how they work together to display your WordPress website.

## Objectives

After completing this lesson, you will be able to:

*   Recognize the fact that many files are needed to make a theme.
*   Explain how various blocks are used in a WordPress theme.

## Prerequisite Skills

You will be better equipped to work through this lesson if you have experience in and familiarity with:

*   Basic knowledge of [installing and activating WordPress themes](https://github.com/wptrainingteam/choosing-and-installing-themes)
*   Basic knowledge of HTML, [CSS](https://github.com/wptrainingteam/introduction-to-css), and [PHP](https://github.com/wptrainingteam/introduction-to-php)

## Assets

*   [Twenty Thirteen theme](http://wordpress.org/themes/twentythirteen)

## Screening Questions

*   Are you familiar with installing and activating themes via the WordPress Dashboard?
*   Will you have a locally or remotely hosted sandbox WordPress site to use during class?
*   Do you have a text editor to view PHP, HTML, CSS, and other files?

## Teacher Notes

*   While there may be "wrong" ways to put together a theme, there is no one "right" way. These examples are very simplistic and not meant to serve as comprehensive guides. There are other, completely valid ways of structuring themes.

## Hands-on Walkthrough

### How a Page is Constructed

WordPress is built to be flexible and builds the pages you see on the screen in blocks. A very common arrangement of these blocks includes the `header.php`, `sidebar.php`, `index.php`, and `footer.php` files and looks like this: 

![WordPress basic page structure](/images/wordpress-basic-structure.png) 

These files (and their corresponding blocks) can be moved around, replaced with other files, have additional files added, or can be removed entirely. For example, an alternative way to arrange the blocks would be. 

![WordPress basic page structure with sidebar on the right](/images/wordpress-basic-structure-sidebarright.png)

So how does WordPress do this? It starts with the URL. Your web browser knows that when you type in www.wordpress.org you're really asking to go to `http://www.wordpress.org/index.php`. All web browsers have default files they look for at a web address, and in the case of a WordPress site that default will be the `index.php` file. So now that WordPress has located the `index.php` file, this is what the code in the world's simplest index.php file looks like: 

```
<?php 
   get_header(); 
   get_sidebar(); 
      if ( have_posts() ) : 
         while ( have_posts() ) : 
            the_post(); 
               the_content(); 
         endwhile; 
      endif; 
   get_footer(); 
?> 
```

Notice that it calls the header (`header.php`), then it calls the sidebar (`sidebar.php`), then it runs the loop and grabs the content, and finally adds the footer (`footer.php`). 

Many themes include much more than these bare minimum files, such as additional stylesheets and JavaScript files. With larger themes it's a good idea to keep files organized using folders. The recommended folder structure in this case should include:

*   `/css/` - additional CSS files, such as `mobile.css`, that the theme uses; NOTE that the `style.css` file must remain in the main theme folder
*   `/js/` - JavaScript files
*   `/img/` - for images that are embedded in the theme such as icons (different than Media Gallery images found in the uploads folder)
*   `/language/` - for translation files

So an example of the files and folder that might be found in a very simple theme could look like: 

![A Theme's Files and Folders Tree Chart](/images/theme-folders-and-files.png)

*   `index.php`
*   `style.css`
*   `/css/`
    *   `mobile.css`
    *   `print.css`
*   ``/img/``
    *   `facebook.png`
    *   `twitter.png`
*   `/js/`
    *   `lightbox.js`
    *   `slider.js`

### The Files Needed to Make a Theme

There are only two basic files **required** to make a WordPress theme:

*   `index.php` Creates the blog.
*   `style.css` Includes styling information for the site.

However, most themes include:

*   `header.php` Generates a page's first elements such as a header image and top level menu.
*   `footer.php` Generates a page'e final elements such as widgets and menus.
*   `sidebar.php` Generates a page's sidebar usually including widgetized areas.
*   `functions.php` Adds features and functions to your site. Works like a WordPress plugin.
*   `screenshot.png` Graphic thumbnail image representing the theme.

And should also include:

*   `single.php` Generates a blog post.
*   `page.php` Generates a static page.
*   `archive.php` Generates a page displaying posts by date published.
*   `category.php` Generates a page displaying posts by category.
*   `tag.php` Generates a page displaying posts by tab.
*   `comments.php` Generates a page displaying posts by comments.

And don't forget:

*   `404.php` Generates a page when a page or post does not exist.
*   `search.php` Generates a page displaying search results.
*   `front-page.php` Used in Settings > Reading to set a static page or the blog as the home page.

That's a lot of PHP files! So how does WordPress know which file to use? That's where the [WordPress Template Hierarchy](https://github.com/wptrainingteam/template-hierarchy) comes in.

## Exercises

1.  Use pseudo-code (an informal high-level description) to outline the files needed to implement the basic structure of a WordPress page that would include a sidebar on the right
2.  Install the [Twenty Thirteen](http://wordpress.org/themes/twentythirteen) theme and examine its files and folder structure

## Quiz

**Which files make up the structure of a basic WordPress page?**

1.  header.php, sidebar.php, index.php, footer.php
2.  header.php, sidebar.php, function.php,footer.php
3.  homepage.php, header.php, index.php, footer.php

**Answer:** 1\. header.php, sidebar.php, index.php, footer.php

* * *

**Which files are **required** for a WordPress theme?**

1.  blog.php, page.php style.css
2.  index.php and style.css
3.  header.php and footer.php

**Answer:** 2\. index.php and style.css

## Additional Resources

[Using Themes](https://codex.wordpress.org/Using_Themes) @ Codex
