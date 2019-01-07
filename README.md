# Widget Areas
## Description

What is a widget area? Why would you add one to your theme? This lesson demonstrates how to add widget areas to your theme and how to add content to these areas.

## Prerequisite Skills

*   Basic knowledge of HTML and PHP
*   Basic knowledge of WordPress [widgets](https://codex.wordpress.org/WordPress_Widgets)
*   Understanding of the [basic file structure of a WordPress theme](https://make.wordpress.org/training/handbook/theme-school/anatomy-of-a-theme/)
*   Understanding of WordPress [child themes](https://make.wordpress.org/training/handbook/theme-school/child-themes/)
*   Ability to manage files with FTP
*   Ability to edit files with a text editor

## Learning Objectives

After completing this lesson, you will be able to:

*   Describe the purpose and functions of widget areas
*   Practice the steps of adding a widget area to a theme
*   Add widgets and content to a new widget area in a site

## Assets

*   [Twenty Sixteen](https://wordpress.org/themes/twentysixteen/) theme

## Screening Questions

*   Are you familiar with using widgets via the WordPress Dashboard?
*   Do you have a basic knowledge of HTML and PHP?
*   Are you able to use FTP and a text editor to edit code files?
*   Do you understand the basic file structure of WordPress, including child themes?

## Teacher Notes

*   Performing a live demo while teaching the steps to add a widget area to a child theme is crucial to having the material "click" for students.
*   It is easiest for students to work on a locally installed copy of WordPress. Set some time aside before class to assist students with installing WordPress locally if they need it. For more information on how to install WordPress locally, please visit our [Teacher Resources page](http://make.wordpress.org/training/teacher-resources/).
*   The preferred answers to the screening questions is "yes." Participants who reply "no" to all 5 questions may not be ready for this lesson.

## Hands-on Walkthrough

### Introduction: What is a Widget Area

Today, you are going to learn how to add widget areas to a WordPress theme. Widget areas are used to create locations in theme template layouts that can hold widget content. In WordPress the terms “sidebar” and “widget area” are related, but may seem confusing. For initial WordPress releases the sidebar could only be stationed on the side, and that’s where the name came from. Over time the requirements became more flexible and it’s now possible to add “sidebars” anywhere in a theme layout, so the name “widget areas” best describes this capability. The management of widgets in widget areas is managed in the **Appearance > Widgets** section of the Dashboard, where widgets can be added to and configured in widget areas with a drag and drop visual interface. In addition to the set of standard WordPress widgets, themes and plugins often provide custom widgets for adding specialized content and functionality.

### Why use widget areas?

WordPress widgets are a powerful means to add content and features that repeat throughout a website, such as category lists, tag clouds, calendars, subscription signup, social media feeds, etc. Widget areas, also known as "widgetized areas" allow themes to manage the placement of repeating widget content in various locations in left or right sidebars, headers, footers, and any other specific section defined by a theme.

### How do widget areas work?

There are three main steps to perform when adding a new widget area to a WordPress theme.

1.  First, for WordPress to recognize a widget area, you need to register a new widget area in the functions.php file. After it’s registered, WordPress will add it as an option for placing widgets.
2.  Next, you need to add the widget area to the desired location in your website's theme. The file you need to modify depends on the location you want the widget to be displayed: header.php, footer.php, index.php, single.php, or another theme template file.
3.  Finally, after the widget area is registered and after it is added to a theme file, you may add widgets to this new area to display on your website.

### Creating a Widget Area

**Scenario:** You want to add a new widget to your website's header section: a calendar for visitors to be able to switch between dates. You are going to create a new widget area in the default WordPress theme [Twenty Sixteen](https://wordpress.org/themes/twentysixteen/). In actual practice, you should always modify a child theme and NOT a parent theme. Also, it's important to make a backup of your site before you make any changes to code files.

#### Step 1: Register a Widget Area

>If you are using a remote sandbox site, you may want to download files via FTP for editing. If you are using a local >sandbox site, you do not need to use FTP. You may use any text editor for this exercise, but do not use a word processor.

Open your theme's functions.php file in your text editor. The file’s path should be: <your root WP folder>/wp-content/themes/twentysixteen. Add the following code to the end of the file and save it when you are finished:

```php
function mytraining_widgets_init() {
  register_sidebar( array(
    'name' => 'Header Sidebar',
    'id' => 'header_sidebar',
    'before_widget' => '<div id="mytraining-widget">',
    'after_widget' => '</div>',
    'before_title' => '<h2>',
    'after_title' => '</h2>', ) );
}
add_action( 'widgets_init', 'mytraining_widgets_init' );
```

You need to choose a name for this add_action function to distinguish it from others, and the function declares an array of values to characterize it. Here are what these values are determine:

*   `name` – the name of the widget area as it will display in the <acronym title="WordPress">WordPress</acronym> administration dashboard
*   `id` – a unique ID for this widget area
*   `description` – description of the widget area
*   `before_widget` – the markup generated before any widgets that will be added later on
*   `after_widget` – the markup generated after any user-added widgets
*   `before_title` – the markup generated before the title of any widgets that will be added later on
*   `after_title` – the markup generated after the title of any user-added widgets

Now if you go to the **Appearance > Widgets** section in your WordPress administration dashboard, you'll see new a new widget area (Header Sidebar) that appears in the list.

#### Step 2: Display the Widget Area

To be able to display the new widget area in the header, you need to edit the theme's header.php. In actual practice, you would determine a proper placement of the widget area in the layout of the header template. For this exercise, you will simply add the new widget area at the bottom of the header, as a proof of concept to test that your new widget area works. Open header.php and add the following line to the bottom of the file:

```php
<?php if ( function_exists('dynamic_sidebar')) { dynamic_sidebar('header_sidebar'); } ?>
```

This code checks that the theme is able to find the sidebar in functions.php, and then it is added to the page. Be sure to save the file with your edits.  

#### Step 3: Adding Content to the Widget Area

Now to add a calendar widget in your website's header, go to **Appearance > Widgets** in the Dashboard and drag **Calendar** to **Header Sidebar**. Type in calendar title and save the changes. Check that your calendar is now displayed in the header area.

### Summary

You have successfully added a new widget area to your website. You or a content manager could continue adding widgets to this widget area. Go forth and conquer!

## Exercises

Practice adding an additional widget area to your website. You may use the following scenario:

*   You need to add a new widget area to the site's footer
*   The widget area needs to add a widget to list your site's most recent comments

## Quiz

**What is the primary purpose of a widget area?**

1.  To replace the outdated sidebar function
2.  To place repeating content and features throughout a website
3.  To embed Facebook comments in a sidebar
4.  To embed media in a post

**Answer:** 2\. To place repeating content and features throughout a website **What is the first step for adding a new widget area?**

1.  Add it to theme's widget.php file
2.  Add it to theme's style.css
3.  Register it in the theme's functions.php
4.  Find a new theme that has the widget area you need

**Answer:** 3\. Register it in the theme's functions.php **Which of the following locations can hold a widget area?**

1.  Theme's sidebar
2.  Theme's footer
3.  Theme's header
4.  All of the above

**Answer:** 4\. All of the above
