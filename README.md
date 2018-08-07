# Wordpress Beadcrumb
Wordpress Breadcrumb Script for your Wordpress Theme.


## Features
* Best practice! Breadcrumb is generated according to Google's recommendations.
* Easy to use!
* Filters available!
* Customizable arguments!


## Getting Started

##### Install with Composer
Add the package to your project's `composer.json`. Visit [getcomposer.org](http://getcomposer.org/) for more information.
```json
{
    "repositories": [
        {
            "url": "https://github.com/w1nte/wp_breadcrumb.git",
            "type": "git"
        }
    ],
    "require": {
        "w1nte/wp_breadcrumb": "dev-master"
    }
}
```

##### Install with NPM
Install the package with `npm install w1nte/wp_breadcrumb`.

##### Install Manually
Download and include the file into your themes `functions.php`
```php 
include_once 'breadcrumb.php';
```


## Usage
##### Basic usage
Use `the_breadcrumb` to display the breadcrumb in your template.
```php
the_breadcrumb([$args]);
```


## Options
You can modify the output with an optional array of arguments. The default options are displayed below.
```php
// Default Config
$breadcrumb = get_breadcrumb(Array(
        'text_domain' => '',
        'delimiter' => ' &raquo; ',
        'home' => 'Home',
        'home_link' => get_bloginfo('url'),
        'before' => '<li itemprop="itemListElement" itemscope itemtype="http://schema.org/ListItem">',
        'after' => '<meta itemprop="position" content="%1$s" /></li>',
        'before_text' => '<span>',
        'after_text' => '</span>',
        'class' => 'breadcrumb',
        'container' => '<nav class="breadcrumb"><ol itemscope itemtype="http://schema.org/BreadcrumbList">%s</ol></nav>'
    ));
```

### Available Functions
* `get_breadcrumb([$args])` returns the html output
* `the_breadcrumb([$args])` prints the html output
##### Examples
```php
$breadcrumb = get_breadcrumb(Array(
    "delimiter" => " / "
);
echo $breadcrumb;
```
```php
the_breadcrumb(Array(
    "delimiter" => " / "
);
```

### Available Filters
* `breadcrumb_args` to manipulate the arguments
* `breadcrumb_html` to manipulate the html output
##### Examples
```php
function breadcrumb_args($args) {
    $args["delimiter"] = " / ";
    return $args;
}
add_filter("breadcrumb_args", "breadcrumb_args", 10, 1);
```
```php
function breadcrumb_html($html) {
    $html .= "<!-- Hello -->";
    return $html;
}
add_filter("breadcrumb_html", "breadcrumb_html", 10, 1);
```



## Example Result
```html
<nav class="breadcrumb">
    <ol itemscope="" itemtype="http://schema.org/BreadcrumbList">
        <li itemprop="itemListElement" itemscope="" itemtype="http://schema.org/ListItem">
            <a href="https://example.io"><span>Home</span></a>
            <meta itemprop="position" content="1">
        </li> 
        » 
        <li itemprop="itemListElement" itemscope="" itemtype="http://schema.org/ListItem">
            <span>Beispiel-Seite</span>
            <meta itemprop="position" content="2">
        </li>
    </ol>
</nav>
```


## Requirements
Tested with Wordpress > 4.9


## License
This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details