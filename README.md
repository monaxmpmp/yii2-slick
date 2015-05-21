yii2-slick
==========
 
Yii2 extension for jQuery Slick Carousel plugin. See more here: [http://kenwheeler.github.io/slick/](http://kenwheeler.github.io/slick/).
 
## Installation
 
You can get this extension through [Composer](https://getcomposer.org/download/).
 
Either run in terminal
 
```Shell
$ php composer.phar require "evgeniyrru/yii2-slick" "*"
```
 
or add
 
```JSON
"evgeniyrru/yii2-slick" : "*"
```
 
to the *require* section of your application's ```composer.json``` file.
 
## Usage
 
This is a common way to run Yii2 widget.
 
```PHP
 
<?php
 
use evgeniyrru\yii2slick\Slick;
use use yii\web\JsExpression;
?>
 
Something html here
 
<?=Slick::widget([

        // HTML tag for container. Div is default.
        'itemContainer' => 'div',
        
        // HTML attributes for widget container
        'containerOptions' => ['class' => 'container'],
        
        // Items for carousel. Empty array not allowed, exception will be throw, if empty 
        'items' => [
            Html::img('/cat_gallery/cat_001.png'),
            Html::img('/cat_gallery/cat_002.png'),
            Html::img('/cat_gallery/cat_003.png'),
            Html::img('/cat_gallery/cat_004.png'),
            Html::img('/cat_gallery/cat_005.png'),
        ],
        
        // HTML attribute for every carousel item
        'itemOptions' => ['class' => 'cat-image'],
        
        // settings for js plugin
        // @see http://kenwheeler.github.io/slick/#settings
        'clientOptions' => [
            'autoplay' => true,
            'dots'     => true,
            // note, that for params passing function you should use JsExpression object
            'onAfterChange' => new JsExpression('function() {console.log("The cat has shown")}'),
        ],
        
    ]); ?>
 
```

If you want to use *breakpoints* feature, type something like this:

```PHP
<?php

use evgeniyrru\yii2slick\Slick;
use use yii\web\JsExpression;

<?=Slick::widget([

        // Widget configuration. See example above.
        
        // settings for js plugin
        // @see http://kenwheeler.github.io/slick/#settings
        'clientOptions' => [
                'dots'     => true,
                'speed'    => 300,
                'autoplay' => true,
                'infinite' => false,
                'slidesToShow' => 4,
                'slidesToScroll' => 4,
                'responsive' => [
                    [
                        'breakpoint' => 1200,
                        'settings' => [
                            'slidesToShow' => 4,
                            'slidesToScroll' => 4,
                            'infinite' => true,
                            'autoplay' => true,
                            'dots' => true,
                        ],
                    ],
                    [
                        'breakpoint' => 992,
                        'settings' => [
                            'slidesToShow' => 4,
                            'slidesToScroll' => 4,
                            'infinite' => true,
                            'autoplay' => true,
                            'dots' => true,
                        ],
                    ],
                    [
                        'breakpoint' => 768,
                        'settings' => [
                            'slidesToShow' => 2,
                            'slidesToScroll' => 2,
                            'infinite' => true,
                            'autoplay' => true,
                            'dots' => true,
                        ],
                    ],
                    [
                        'breakpoint' => 480,
                        'settings' => 'unslick', // Destroy carousel, if screen width less than 480px
                    ],

                ],
        ],
        
    ]); ?>

?>
```

## Issues

If some problems occurred, you can create [issue](https://github.com/EvgeniyRRU/yii2-slick/issues).

Thank you for attention.