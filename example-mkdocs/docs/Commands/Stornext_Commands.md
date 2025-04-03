## Commands

login to root
```
sudo rootsh
```

## Log Files
Generally there is quite a bit of information in the System log files with regard to stornext, but it also has its own log files that can provide more detailed information, the most useful of these are:

/usr/adic/TSM/logs/tac/tac_00
This contains information about all TSM activities, and it can be a bit of a headache to decipher what is going on. 

/usr/adic/TSM/logs/trace/trace_01
This is updated after every store or retrieve, and although it does not contain the filenames or filesystems involved, it does show the tape used, the mover used, the size of files and the transfer rate.

/usr/adic/MSM/logs/history/hist_00
This is updated for every tape mount and dismount and contains time, tape number and drive number.

/usr/adic/TSM/logs/tac/backup.log
A Full backup is run every Sunday night, and a partial on all other nights. The full backup process is recorded in this log file and should be looked at if there are any problems.

## Tapes 
The following commands are all to do with tape activity and can be helpful when tracking problems.

```
fsstate
```
This command shows the tape drives, their status, and the tapes mounted on them.

		fsmedinfo tapnum
Gives information on the Media with relation to the HSM such as available unavailable, suspect , number of files on tape
		fsmedinfo -l  media        
 gives the above info plus a full list of files on tape. 
		vsmedqry media
Gives information on the media with relation to the archive such as which archive – i6k_archive2 (the robot)  or vault1 (anywhere else  such as tape racks)


# Class/policy commands

fsaddclass  <classname>  -  Created new class/policy with default policy options set.

fsmodclass  <classname>  [options] -  Change options for the class/policy

fsaddrelation -c <classname> <directory>  -  add class/policy to directory, thus making it managed. best done when directory is empty.

File manipulation

fsstore [-c n ]  filename   -  manually store n number of copies of a file

fsretrieve -a filenam  -  retrieve file

# Operator Task Scripts

/usr/adic/pcg/available_tapes – provides the number of blank tapes available in the robot
/usr/adic/pcg/i6k_enter_blanktapes – takes no parameters and will enter any tapes that have been placed in the I/E stations into the robot as blank tapes.
/usr/adic/pcg/i6kqry – provides the number of empty slots in the robot.
/usr/adic/pcg/eject_i6k – Will eject a set number of tapes from the robot to free up space. Tapes picked according to the time they were last accessed – oldest first.
 /usr/adic/pcg/enter_tape_i6k – takes a tape number as a parameter, and will enter it from an I/E station into the robot when requested.
/usr/adic/pcg/check_i6k_moves – returns any tapes that need to be moved from vault to robot.
 /usr/adic/pcg/enter_recycled_tapes – Instead of using new tapes, this script will list 20 pre-used but now empty tapes, (if any available) that can be put into the I/E station. The script will then enter the tapes as blanks.