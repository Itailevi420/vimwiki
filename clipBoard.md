## clear the CLIPBOARD on gnome
_https://www.reddit.com/r/gnome/comments/qyuk7i/is_there_a_way_to_clear_gnome_clipboard_from/_

If you’re on Xorg:
    ```sh
          xsel -cb  # to clear the CLIPBOARD and
          xsel -cp  # to clear the PRIMARY selection.
    ```
If you’re on Wayland:
    ```sh
          wl-copy -c   # to clear the CLIPBOARD
          wl-copy -cp  # to clear the PRIMARY selection.
    ```
