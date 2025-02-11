---
title: 'Custom Date-Specific Product Badges'
date: 2024-06-04T01:47:00.008+06:00
draft: false
tags: ['wordpress']
---

[![](https://blogger.googleusercontent.com/img/a/AVvXsEjzQcnP39aCzmn8fidInHmnPwldHpKHtD8cB5KdEbHjFSQ0CN7ol0JIpUsizsMDy02R1hti_YTLFl6bCRiC4B00H6skLr_P88Ju47QQpUVVLjmSov4X1JSpZHJTHUma9DlmLMxa9DHPBuJshfRBNFpPrCdZjurNa-T7lrPGivgvmuO1ouhZ4qzgPM-tkbnt)](https://blogger.googleusercontent.com/img/a/AVvXsEjzQcnP39aCzmn8fidInHmnPwldHpKHtD8cB5KdEbHjFSQ0CN7ol0JIpUsizsMDy02R1hti_YTLFl6bCRiC4B00H6skLr_P88Ju47QQpUVVLjmSov4X1JSpZHJTHUma9DlmLMxa9DHPBuJshfRBNFpPrCdZjurNa-T7lrPGivgvmuO1ouhZ4qzgPM-tkbnt)

  
  

 // Add custom fields to WooCommerce backend under General tab

add\_action( 'woocommerce\_product\_options\_general\_product\_data', 'wpsh\_add\_text\_field\_below\_sale\_price' );

function wpsh\_add\_text\_field\_below\_sale\_price() {

    global $product\_object;

    // Original custom field

    woocommerce\_wp\_text\_input( array(

        'id'            => '\_badge',

        'label'         => \_\_( 'Badge text', 'woocommerce' ),

        'description'   => \_\_( 'Enter your pduct badge text here', 'woocommerce' ),

        'desc\_tip'      => 'true',

        'type'          => 'text',

        'value'         => $product\_object->get\_meta( '\_badge' ),

    ) );

    // Start date field

    woocommerce\_wp\_text\_input( array(

        'id'                => '\_start\_date',

        'label'             => \_\_( 'Dislay start date', 'woocommerce' ),

        'placeholder'       => 'YYYY-MM-DD',

        'description'       => \_\_( 'Enter the start date of the badge display', 'woocommerce' ),

        'type'              => 'date',

        'value'             => $product\_object->get\_meta( '\_start\_date' ),

        'custom\_attributes' => array(

            'pattern'   => '\\d{4}-\\d{2}-\\d{2}',

        ),

    ) );

    // End date field

    woocommerce\_wp\_text\_input( array(

        'id'                => '\_end\_date',

        'label'             => \_\_( 'Display end date', 'woocommerce' ),

        'placeholder'       => 'YYYY-MM-DD',

        'description'       => \_\_( 'Enter the start date of the badge displayv', 'woocommerce' ),      

        'type'              => 'date',

        'value'             => $product\_object->get\_meta( '\_end\_date' ),

        'custom\_attributes' => array(

            'pattern'   => '\\d{4}-\\d{2}-\\d{2}',

        ),

    ) );

}

  

// Save custom field values including dates for all product types

add\_action( 'woocommerce\_admin\_process\_product\_object', 'wpsh\_save\_field', 10, 1 );

function wpsh\_save\_field( $product ) {

    if ( isset( $\_POST\['\_badge'\] ) ) {        

        $product->update\_meta\_data( '\_badge', sanitize\_text\_field( $\_POST\['\_badge'\] ) );

    }

    if ( isset( $\_POST\['\_start\_date'\] ) ) {

        $product->update\_meta\_data( '\_start\_date', sanitize\_text\_field( $\_POST\['\_start\_date'\] ) );

    }

    if ( isset( $\_POST\['\_end\_date'\] ) ) {

        $product->update\_meta\_data( '\_end\_date', sanitize\_text\_field( $\_POST\['\_end\_date'\] ) );

    }

    $product->save();

}

  

// Adjust display logic on single product and archive pages

function wpsh\_should\_display\_custom\_field($start\_date, $end\_date, $text) {

    $current\_date = date('Y-m-d');

    if (empty($start\_date) && empty($end\_date) && !empty($text)) {

        return true;

    } elseif (!empty($start\_date) && empty($end\_date) && $current\_date >= $start\_date) {

        return true;

    } elseif (empty($start\_date) && !empty($end\_date) && $current\_date <= $end\_date) {

        return true;

    } elseif (!empty($start\_date) && !empty($end\_date) && $current\_date >= $start\_date && $current\_date <= $end\_date) {

        return true;

    }

    return false;

}

  

add\_action( 'woocommerce\_before\_add\_to\_cart\_form', 'wpsh\_display\_on\_single\_product\_page', 1 );

function wpsh\_display\_on\_single\_product\_page() {

    global $product;

    if ( is\_a( $product, 'WC\_Product' ) ) {

        $text = $product->get\_meta( '\_badge' );

        $start\_date = $product->get\_meta( '\_start\_date' );

        $end\_date = $product->get\_meta( '\_end\_date' );

        if ( wpsh\_should\_display\_custom\_field($start\_date, $end\_date, $text) ) {

            echo '<div class="woocommerce-message"> ' . $text . '</div>';

        }

    }

}

  

add\_action( 'blocksy:woocommerce:product-card:title:after', 'wpsh\_display\_on\_archive\_page', 10 );

function wpsh\_display\_on\_archive\_page() {

    global $product;

    if ( is\_a( $product, 'WC\_Product' ) ) {

        $text = $product->get\_meta( '\_badge' );

        $start\_date = $product->get\_meta( '\_start\_date' );

        $end\_date = $product->get\_meta( '\_end\_date' );

      if (wpsh\_should\_display\_custom\_field($start\_date, $end\_date, $text)) {

    echo '<div class="custom-text"> ' . $text . '</div>';

}

}

}