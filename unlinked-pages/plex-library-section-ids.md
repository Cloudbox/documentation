# Plex-Library-Section-IDs.md

This guide will take you through retrieving your Plex Library Section IDs.

_Note: For Mediabox / Feederbox setup, the following will be done on the Mediabox._

1. Run the following command:

   ```text
   /opt/plex_autoscan/scan.py sections
   ```

   _Note: If you get an error here, see the \[\[FAQ\|FAQ\#fix-permission-issues-with-plex-logs\]\] on how to fix permissions._

2. Script output
   * The script output will show your Plex Library Section IDs in the format of:

     ```text
      SECTION ID: LIBRARY NAME
     ```

   * For simple libraries, your section IDs may look like this:

     ```text
     1: Movies
     2: TV
     ```

* For more advanced libraries, your section IDs may look like this:

  ```text
  1: 3D
  2: 4K
  3: Foreign
  4: Hollywood
  5: Kids
  6: TV
  ```

  _Note: Your Plex Library Section IDs will be different as it is based on the order you added them in Plex._

