---
title: 'Daraz Mall'
date: 2024-05-01T21:37:00.003+06:00
draft: false
url: /2024/05/daraz-mall.html
tags: 
- wordpress
---

// Add custom meta field for marking product as plaza  
add\_action( 'woocommerce\_product\_data\_panels', 'add\_plaza\_product\_field' );  
function add\_plaza\_product\_field() {  
    global $post;  
    // Check if product type is simple or grouped    if ( in\_array( $post->post\_type, array( 'product', 'product\_variation' ) ) ) {        // For simple products        if ( ! $post->post\_parent ) {            woocommerce\_wp\_checkbox(                array(                    'id' => '\_is\_plaza\_product',                    'label' => \_\_( 'Mark as Plaza Product', 'woocommerce' ),                    'description' => \_\_( 'Check this box if this product is plaza.', 'woocommerce' ),                    'desc\_tip' => true,                    'value' => get\_post\_meta( $post->ID, '\_is\_plaza\_product', true )                )            );        }  
        // For grouped products        elseif ( $post->post\_parent && get\_post\_type( $post->post\_parent ) === 'product' ) {            woocommerce\_wp\_checkbox(                array(                    'id' => '\_is\_plaza\_product\_grouped',                    'label' => \_\_( 'Mark as Plaza Product', 'woocommerce' ),                    'description' => \_\_( 'Check this box if this grouped product is plaza.', 'woocommerce' ),                    'desc\_tip' => true,                    'value' => get\_post\_meta( $post->ID, '\_is\_plaza\_product\_grouped', true )                )            );        }    }}  
// Save custom meta field value for simple products  
add\_action( 'woocommerce\_process\_product\_meta', 'save\_plaza\_product\_field' );  
function save\_plaza\_product\_field( $product\_id ) {  
    $is\_plaza\_product = isset( $\_POST\['\_is\_plaza\_product'\] ) ? 'yes' : 'no';    update\_post\_meta( $product\_id, '\_is\_plaza\_product', $is\_plaza\_product );  
    // If product is marked as plaza, assign it to "Plaza" category    if ( $is\_plaza\_product === 'yes' ) {        $term = get\_term\_by( 'name', 'Plaza', 'product\_cat' );        if ( $term && ! is\_wp\_error( $term ) ) {            wp\_set\_object\_terms( $product\_id, $term->term\_id, 'product\_cat', true );        }    }}  
// Save custom meta field value for grouped products  
add\_action( 'woocommerce\_process\_product\_meta\_grouped', 'save\_plaza\_product\_field\_grouped' );  
function save\_plaza\_product\_field\_grouped( $product\_id ) {  
    $is\_plaza\_product\_grouped = isset( $\_POST\['\_is\_plaza\_product\_grouped'\] ) ? 'yes' : 'no';    update\_post\_meta( $product\_id, '\_is\_plaza\_product\_grouped', $is\_plaza\_product\_grouped );  
    // If product is marked as plaza, assign it to "Plaza" category    if ( $is\_plaza\_product\_grouped === 'yes' ) {        $term = get\_term\_by( 'name', 'Plaza', 'product\_cat' );        if ( $term && ! is\_wp\_error( $term ) ) {            wp\_set\_object\_terms( $product\_id, $term->term\_id, 'product\_cat', true );        }    }}  
// Add link around the image and title for plaza products  
add\_filter( 'the\_title', 'add\_plaza\_mark\_to\_title', 10, 2 );  
function add\_plaza\_mark\_to\_title( $title, $id ) {  
    // Check if the title is being displayed in the frontend    if ( ! is\_admin() ) {        $is\_plaza\_product = get\_post\_meta( $id, '\_is\_plaza\_product', true );        if ( $is\_plaza\_product === 'yes' ) {            $image\_url = 'https://noorexpress.shop/wp-content/uploads/2021/08/brand-alessi.png';            $image\_target\_url = 'https://noorexpress.shop/plaza/';            $product\_permalink = get\_permalink( $id );            $title = '<a href="' . $image\_target\_url . '"><img src="' . $image\_url . '" alt="Plaza Product" class="plaza-image" /></a><a href="' . $product\_permalink . '">' . $title . '</a>';        }    }    return $title;}  
x