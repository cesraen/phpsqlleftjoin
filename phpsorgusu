 <?php 
        $sql = "SELECT event_id, event_name, event_date, event_image, location FROM events";
    $stmt = $baglanti->prepare($sql);
    $stmt->execute();
    $events = $stmt->fetchAll(PDO::FETCH_ASSOC);
    

    ?><?php foreach ($events as $event): ?>
        <?php
        $event_idsi = $event['event_id'];
        $sql = "SELECT link_title FROM links WHERE event_id = :event_idsi";
        $stmt = $baglanti->prepare($sql);
        $stmt->execute(["event_idsi" => $event_idsi]);
        $link = $stmt->fetch(PDO::FETCH_ASSOC);
        
        if (!$link) {
            // // Eğer veri yoksa 404 hatası gönder ve sayfayı sonlandır
            // echo "aga 1"; // 404 sayfasını include et
            // exit();
        }
        $gelen_baslik = $link['link_title'];

        // Tarih formatını "11 AĞU" formatına dönüştürmek için PHP kodu
        $date = new DateTime($event['event_date']);
        $day = $date->format('d');
        
        // Ay adını 'AĞU' formatında almak için bir dizi kullanarak manuel bir dönüşüm yapıyoruz
        $months = [
            1 => 'OCA', 2 => 'ŞUB', 3 => 'MAR', 4 => 'NİS', 5 => 'MAY', 6 => 'HAZ',
            7 => 'TEM', 8 => 'AĞU', 9 => 'EYL', 10 => 'EKİ', 11 => 'KAS', 12 => 'ARA'
        ];
        $month = $months[(int)$date->format('m')];
        ?>
    
        <a href="/etkinlik/<?=$gelen_baslik ?>" class="event week">
            <img src="<?php echo htmlspecialchars($event['event_image'] ?? 'default.jpg'); ?>" alt="<?php echo htmlspecialchars($event['event_name'] ?? 'Event'); ?>">
            <div class="event-info">
                <span class="latest-date"><?php echo $day . ' ' . $month; ?></span>
                <span class="artist"><?php echo htmlspecialchars($event['event_name'] ?? 'Event'); ?></span>
                <span class="location"><?php echo htmlspecialchars($event['location'] ?? ''); ?></span>
            </div>
        </a>
    <?php endforeach; ?>
<?php echo "ikinci yöntem"; ?>
<?php 
$sql = "SELECT e.event_name, e.event_date, e.event_image, e.location, l.link_title 
        FROM events e 
        LEFT JOIN links l ON e.event_id = l.event_id";
$stmt = $baglanti->prepare($sql);
$stmt->execute();
$events = $stmt->fetchAll(PDO::FETCH_ASSOC);
?>
<?php foreach ($events as $event): ?>
    <?php
    // Tarih formatını "11 AĞU" formatına dönüştürmek için PHP kodu
    $date = new DateTime($event['event_date']);
    $day = $date->format('d');
    
    // Ay adını 'AĞU' formatında almak için manuel bir dönüşüm yapıyoruz
    $months = [
        1 => 'OCA', 2 => 'ŞUB', 3 => 'MAR', 4 => 'NİS', 5 => 'MAY', 6 => 'HAZ',
        7 => 'TEM', 8 => 'AĞU', 9 => 'EYL', 10 => 'EKİ', 11 => 'KAS', 12 => 'ARA'
    ];
    $month = $months[(int)$date->format('m')];
    ?>
    
    <a href="/etkinlik/<?php echo htmlspecialchars($event['link_title'] ?? ''); ?>" class="event week">
        <img src="<?php echo htmlspecialchars($event['event_image'] ?? 'default.jpg'); ?>" alt="<?php echo htmlspecialchars($event['event_name'] ?? 'Event'); ?>">
        <div class="event-info">
            <span class="latest-date"><?php echo $day . ' ' . $month; ?></span>
            <span class="artist"><?php echo htmlspecialchars($event['event_name'] ?? 'Event'); ?></span>
            <span class="location"><?php echo htmlspecialchars($event['location'] ?? ''); ?></span>
        </div>
    </a>
<?php endforeach; ?>
