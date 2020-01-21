# 2performant-wordpress
Implementare 2performant pe wordpress


// i used Snippet Plugin
// code for  single product...

add_action( 'wp_footer', 'my_footer_scripts' );
function my_footer_scripts(){
// atunci cand se face plata cu cardul la mobilpayment ... 
	if( isset( $_GET['order_id'] )  && is_wc_endpoint_url( 'order-received' ) ) {
		$order_id = $_GET['order_id'];
		
		if ( ! empty( $order_id ) ) {
			$order = wc_get_order( $order_id );
			$total = $order->get_total();
			
			$items = $order->get_items();
			foreach ( $items as $item ) {
				$product_name = $item['name'];
				$product_id = $item['product_id'];
				$product_variation_id = $item['variation_id'];
			}
			
			
  ?>
  
	  <iframe height='1' width='1' scrolling='no' marginheight='0' marginwidth='0' frameborder='0' src='https://event.2performant.com/events/salecheck?amount=<?php echo $total; ?>&campaign_unique=-AICI PUNE CODUL TAU-&confirm=-AICI PUNE CODUL TAU-&description=<?php echo $product_name; ?>&transaction_id=<?php echo $order_id; ?>'></iframe>
  <?php
		}
	}
}

// done. 

