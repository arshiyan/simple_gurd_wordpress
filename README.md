### simple gurd for Wordpress developer
Its a simple gurd for wordpress developer


just copy and paste this code to your function.php and then you can down and up your website by url


for display alarm 
> for display alarm 
your-website.com/?gurd=startyour-website.com/?gurd=start

and for unblock website 
> and for unblock website 
your-website.com/?gurd=stopyour-website.com/?gurd=stop


    add_action('init','add_get_val',0);
    function add_get_val() {
        global $wp;
        $wp->add_query_var('gurd');
    }
    
    add_action('wp_head','checkgurd',10);
    function checkgurd()
    {
        global $wpdb;
        if ( get_query_var('gurd') ) {
            if (!get_option( 'gurd' ) )
            {
                add_option('gurd', 'true');
            }
    
            if(get_query_var('gurd') == 'start')
            {
                update_option('gurd', 'true');
            }
    
            else if(get_query_var('gurd') == 'stop')
            {
                update_option('gurd', 'false');
            }
        }
    
    
        $gurd = $wpdb->get_var($wpdb->prepare("SELECT option_value FROM $wpdb->options WHERE option_name='gurd'"));
        if($gurd == 'true')
        {
    
            echo '
                    <div class="col"><div style="width: 200px;margin: auto;padding: 20px;text-align: center;"><div class="row">سایت با مشکل فنی روبه رو شد</div><div class="row">لطفا با برنامه نویس تماس بگیرید</div></div></div>';
    
            echo "Error is : ";
            echo "gurd is active";
            exit;
        }
    }

you can change start and stop by your string for example 

for display alarm 
> for display alarm 
your-website.com/?gurd=startyour-website.com/?gurd=aljsdkfjhakjsdhf

and for unblock website 
> and for unblock website 
your-website.com/?gurd=stopyour-website.com/?gurd=kljshdkfhskljhdk




###End
