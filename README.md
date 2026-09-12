# SoundCloud ID Extractor & Player Integration

A toolkit for extracting SoundCloud track/playlist IDs from embed codes and integrating SoundCloud music into web pages.

## Features

- **ID Extractor**: Parse SoundCloud iframe embed codes to extract track or playlist IDs
- **Music Player UI**: Fully styled player with animated disc, play/pause controls
- **Double URL Decoding**: Handles encoded SoundCloud URLs automatically
- **Type Detection**: Automatically identifies track vs playlist IDs

## SoundCloud ID Extractor

Paste a SoundCloud iframe embed code below to extract the track or playlist ID.

### Usage

1. Open `soundcloud_ID_Extractor.html` in a browser
2. Paste the SoundCloud iframe `src` code into the textarea
3. Click **Extract ID**
4. The extracted ID and type (Track/Playlist) will display below

### How it works

1. Extracts the `src` attribute from the iframe
2. Retrieves the `url` parameter from the query string
3. Decodes the URL twice (handles URL-encoded characters)
4. Matches against `tracks/\d+` or `playlists:\d+` patterns

## SoundCloud Player Integration

Integrate SoundCloud music into your website with this ready-to-use player.

### Integration

Copy the following code into your HTML where you want the player to appear:

```html
<!-- SOUNDTRACK PLAYER -->
<script src="https://w.soundcloud.com/player/api.js"></script>

<style>
.music{
    position:fixed;
    bottom:20px;
    left:20px;
    display:flex;
    align-items:center;
    gap:15px;
    z-index:999;
}

.disc{
    width:80px;
    height:80px;
    border-radius:50%;
    overflow:hidden;
    border:2px solid gold;
    box-shadow:0 0 25px rgba(255,215,0,.4);
}

.disc img{
    width:100%;
    height:100%;
    object-fit:cover;
}


.rotate{
    animation:spin 6s linear infinite;
}


@keyframes spin{
    from{
        transform:rotate(0deg);
    }
    to{
        transform:rotate(360deg);
    }
}


.music button{
    padding:10px 18px;
    border:none;
    border-radius:25px;
    cursor:pointer;
    background:linear-gradient(90deg,#d4af37,#fff3b0,#d4af37);
    font-weight:bold;
}
</style>


<!-- Hidden SoundCloud Player -->
<iframe 
id="sc-player"
width="100%"
height="166"
scrolling="no"
frameborder="no"
allow="autoplay"
style="display:none;"
src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/19087066&auto_play=false">
</iframe>


<!-- Music UI -->
<div class="music">

    <div class="disc" id="disc">
        <img src="img6.jpg">
    </div>


    <button id="musicBtn" onclick="toggleMusic()">
        🎵 Play Song
    </button>

</div>


<script>

const iframe = document.getElementById("sc-player");

const soundcloud = SC.Widget(iframe);

let playing = false;


function toggleMusic(){

    const btn = document.getElementById("musicBtn");
    const disc = document.getElementById("disc");


    if(playing){

        soundcloud.pause();

        disc.classList.remove("rotate");

        btn.innerHTML = "🎵 Play Song";

        playing = false;


    }else{



        soundcloud.play();

        disc.classList.add("rotate");

        btn.innerHTML = "⏸ Pause Song";

        playing = true;

    }
}
</script>
```

### Customization

- Replace `https://api.soundcloud.com/tracks/19087066` with your desired track/playlist URL
- Modify the `img src` attribute to change the album art
- Adjust the CSS positions/colors to match your site design
- Change the button text and icons as needed

## Files

| File | Description |
|------|-------------|
| `soundcloud_ID_Extractor.html` | Tool to extract SoundCloud track/playlist IDs from embed codes |
| `soundcloud_intergration.txt` | Complete HTML/CSS/JS for SoundCloud player integration |
| `README.md` | This file |

## License

This project is open source and available for personal use.