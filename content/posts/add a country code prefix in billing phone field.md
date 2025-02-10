---
title: 'add a country code prefix in billing phone field'
date: 2024-06-04T01:43:00.006+06:00
draft: false
tags: ['wordpress']
---
```
> // Add country calling code prefix in woocommerce billing phone  
> // Register WordPress hooks and callbacks for the WooCommerce checkout.  
> add\_action( 'wp\_footer', 'wpsh\_add\_callback\_script' );  
> add\_action( 'wp\_ajax\_nopriv\_append\_country\_prefix\_in\_billing\_phone', 'wpsh\_add\_phone\_prefix' );  
> add\_action( 'wp\_ajax\_append\_country\_prefix\_in\_billing\_phone', 'wpsh\_add\_phone\_prefix' );  
> add\_action( 'woocommerce\_checkout\_process', 'wpsh\_validate\_phone' );  
> /\* Outputs the JavaScript required for updating the billing phone with the country prefix. \*/  
> function wpsh\_add\_callback\_script() {  
>     // Securely pass data to JavaScript.    $ajax\_url = admin\_url('admin-ajax.php');    ?>    <script type="text/javascript">        (function($) {            $(document.body).on('updated\_checkout', function() {                var country\_code = $('#billing\_country').val();                var ajax\_data = {                    action: 'append\_country\_prefix\_in\_billing\_phone',                    country\_code: country\_code                };                $.post('<?php echo esc\_js($ajax\_url); ?>', ajax\_data, function(response) {                    $('#billing\_phone').val(response);                });            });        })(jQuery);    </script>    <?php}  
> /\* Handles AJAX request to append the country calling code to the billing phone field. \*/  
> function wpsh\_add\_phone\_prefix() {  
>     $country\_code = isset($\_POST\['country\_code'\]) ? sanitize\_text\_field($\_POST\['country\_code'\]) : '';    $calling\_code = '';    if ($country\_code) {        $calling\_codes = WC()->countries->get\_country\_calling\_code($country\_code);        $calling\_code = is\_array($calling\_codes) ? $calling\_codes\[0\] : $calling\_codes;    }    echo $calling\_code;    wp\_die(); }  
> /\* Validates the phone number length during the WooCommerce checkout process. \*/  
> function wpsh\_validate\_phone() {  
>     if (isset($\_POST\['billing\_phone'\]) && strlen(preg\_replace('/\[^0-9\]/', '', $\_POST\['billing\_phone'\])) < 6) {        wc\_add\_notice(\_\_('Billing Phone must be at least 6 digits long.', 'woocommerce'), 'error');    }}
```