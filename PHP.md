# PHP

### Adding ID to each element on PHP
```sh
$count = 0; // 0+1
foreach($schedule_tabs as $tab) :
$count++;
echo $count; // 1
endforeach;

if($sched_count1 > 1) {
   break;
 } // stop the loop if count greater 1;

$schedule_tabs[0]['tab'] // accessing array within array
array_slice($schedule_tabs, 1) // starts loop at the second value```


### Get Ordinal and days in JP
```sh
function ordinal($number) {
    $ends = array('th','st','nd','rd','th','th','th','th','th','th');
    if ((($number % 31) >= 11) && (($number % 31) <= 13)) {
        return 'th';
    } else {
        return $ends[$number % 10];
    }
}

function daysInJP($event) {
    $sched_day = $event->format('D');

    switch($sched_day) {
      case 'Mon':
        echo '（月）';
        break;
      case 'Tue':
        echo '（火）';
        break;
      case 'Wed':
        echo '（水）';
        break;
      case 'Thu':
        echo '（木）';
        break;
      case 'Fri':
        echo '（金）';
        break;
      case 'Sat':
        echo '（土）';
        break;
      case 'Sun':
        echo '（日）';
        break;
      default:
        echo '';
    }
}
```

### Date Filter
```sh
function get_news_years() {
    $args = array(
        'post_type' => NEWS_POST_TYPE,
        'order' => 'DESC',
        'post_status' => 'publish',
        'posts_per_page' => -1,
    );

    $news_query = new WP_Query( $args );

    foreach( $news_query->posts as $news_year ) {
        $post_years[] = date( 'Y', strtotime( $news_year->post_date ));
    }

    return array_unique( $post_years );
}
```
