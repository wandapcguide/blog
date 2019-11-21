---
title: "Show album art on ncmpcpp"
date: 2017-12-05T13:56:41+07:00
draft: false
---

okey in this article, i wanna show you how to make your ncmpcpp look beauty like your girlfriend. that its how to show album arts on ncmpcpp, its possible to show casue you don't need again album text statement. but, now you can look album picture when your play music on ncmpcpp.

this my ncmpcpp
<center><img class="special-img-class" src="/albumart-ncmpcpp/1.png" /></center>

okey lets move into step.

<p>1. copy this scritp into your ~/.ncmpcpp/config</p>

```
% egrep -v '^#' .ncmpcpp/config

mpd_music_dir = "/home/user/Music/"


mpd_host = "127.0.0.1"

mpd_port = "6601"

mouse_list_scroll_whole_page = "yes"

lines_scrolled = "1"


visualizer_in_stereo = "no"

visualizer_fifo_path = "/tmp/mpd.fifo"

visualizer_output_name = "my_fifo"

visualizer_sync_interval = "10"

visualizer_type = "spectrum"

visualizer_look = "▋▋"


message_delay_time = "3"

playlist_shorten_total_times = "yes"

playlist_display_mode = "classic"

browser_display_mode = "columns"

search_engine_display_mode = "columns"

playlist_editor_display_mode = "columns"

autocenter_mode = "yes"

centered_cursor = "yes"

user_interface = "classic"

follow_now_playing_lyrics = "yes"

locked_screen_width_part = "60"

display_bitrate = "no"

external_editor = "nano"


main_window_highlight_color = "white"


progressbar_elapsed_color = "white"

progressbar_color = "black"


#progressbar_look = "▃▃▃"

progressbar_look = "─⊙ "


mouse_support = "yes"

header_visibility = "no"

statusbar_visibility = "no"


statusbar_color = "white"

visualizer_color = "white"

titles_visibility = "no"

enable_window_title = "yes"


now_playing_prefix = "$b"

now_playing_suffix = "$8$/b"


#now_playing_prefix = "$u$2"

#now_playing_suffix = "$2$/u$2"


song_columns_list_format = "(6)[]{} (23)[red]{a} (26)[yellow]{t|f} (40)[green]{b} (4)[blue]{l}"


color1 = "white"

color2 = "black"


song_list_format = " $5%l  $7%t $R$5%a "


#uncomment both statement's below if you want to display the albumart


execute_on_song_change="~/.ncmpcpp/art.sh"

song_list_format = "                               $2%t $R$5%a "


song_status_format = "$b$7♫ $2%a $4⟫$3⟫ $8%t $4⟫$3⟫ $5%b "

song_window_title_format = " {%a} - {%t}"
```
<p>2. and copy this code and save as art.sh to ~/ncmpcpp and making that script is executable by use that command chmod +x art.sh</p>

```
#!/bin/bash
#put this file to ~/.ncmpcpp/

MUSIC_DIR=/media/dante/deb/Sounds/ #path to your music dir

COVER=/tmp/cover.jpg

function reset_background
{
    printf "\e]20;;100x100+1000+1000\a"

}

{

    album="$(mpc -p 6601 --format %album% current)"

    file="$(mpc -p 6601 --format %file% current)"

    album_dir="${file%/*}"

    [[ -z "$album_dir" ]] && exit 1

    album_dir="$MUSIC_DIR/$album_dir"


    covers="$(find "$album_dir" -type d -exec find {} -maxdepth 1 -type f -iregex ".*/.*\(${album}\|cover\|folder\|artwork\|front\).*[.]\(jpe?g\|png\|gif\|bmp\)" \; )"

    src="$(echo -n "$covers" | head -n1)"

    rm -f "$COVER"

    if [[ -n "$src" ]] ; then

        #resize the image's width to 300px

        convert "$src" -resize 300x "$COVER"

        if [[ -f "$COVER" ]] ; then

           #scale down the cover to 30% of the original

           printf "\e]20;${COVER};70x70+0+00:op=keep-aspect\a"

        else

            reset_background

        fi

    else

        reset_background

    fi

} &
```
<p>3. in the art.sh look into MUSIC_DIR line and set the variable to your music dir. example:</p>

```
 MUSIC_DIR=/media/dante/deb/Sounds/
```

<p>4. assure, you have a album art picture in your music dir . i suggest, to make sub folder for your music with same album. like this, and dont forget to rename your picture album to cover.jpg</p>

<center><img class="special-img-class" src="/albumart-ncmpcpp/2.png" /></center>

<p>5. the dependecies you must have is mpc and imagemagick. at here i use 6601 port on my mpc and mpd, so you can change it to your port how much you use</p>

and bingo, if you got flick on urxvt just adjust the geometry.


yeah that its, if you have question, comment , and thanks, just comment below. lets disqus. 