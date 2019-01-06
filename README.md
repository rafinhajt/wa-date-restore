# WhatsApp image date restore
A simple command line tool for restoring the EXIF creation date of WhatApp images.

I ran into an issue where the original dates of my WhatsApp images where lost after restoring them from Google Drive Backup. 
This program lets you restore these dates by **extracting the original date from the filename**. 
Since the filenames follow a specific pattern `IMG-<date>-WA<number>.<extension>` (e.g. IMG-20160315-WA0020.jpg), we can 
extract the creation date (more precisely the date when the image was received) and write it back into the file.

## Usage
* Download the Zip file from the releases page and extract it
* Open a terminal and navigate into `/bin`
* Start the program by typing `./wa-date-restore` (on Linux or OSX) or `wa-date-restore.dat` (on Windows)
    * Define the input folder with `-d <path>`
    * Activate EXIF date overwrite with `-e`
    
All files contained in the input directory will be processed and then saved into the folder `/wa_date_restored` inside 
the input directory.

### Program Arguments
```
Usage: wa-date-restore [-d <path>] [-e] [-h] [-l]

 -d,--directory <path>   Full path to the directory in which all files
                         should be processed.
 -e,--exifDate           Overwrite the EXIF "DateTimeOriginal" and
                         "DateTimeDigitized" tag with the extracted date.
                         (This is what you normally want to do.)
 -h,--help               Print this help message.
 -l,--lastModifiedDate   Overwrite the "Last Modified Date" with the
                         extracted date.
```

### Usage Example
```bash
user@Tower-Mint ~/Desktop/wa-date-restore-1.0.1/bin $ ./wa-date-restore -d /home/user/Downloads/Photos -e
Processing IMG-20160315-WA0021.jpg: [EXIF Date -> 15.03.2016 12:00:00]
Processing IMG-20160315-WA0018.jpg: [EXIF Date -> 15.03.2016 12:00:00]
Processing IMG-20160315-WA0020.jpg: [EXIF Date -> 15.03.2016 12:00:00]
user@Tower-Mint ~/Desktop/wa-date-restore-1.0.1/bin $ 
```
Now the EXIF date tags have been set to the extracted date:
![EXIF Date](https://i.ibb.co/Tbcqtz0/Screenshot-Exif.png "EXIF Properties")

## Contribution
If you have any questions or run into problems, please open an issue. Feel free to contribute to this project by opening 
a pull request or forking the repository.