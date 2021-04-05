# Q-Cuts CSV Template files

Use these template files to add CSV filters to the Q-Cuts cue sheet generation extension for Adobe Premiere.

Because of some of the formatting that's built in to the .xlsx template, it is highly recommended that you work in that version of the template in Excel and then save it as a CSV for import into Q-Cuts. To do this, in Excel, go to File>Save As and under "File Format," select "CSV UTF-8." Excel might flash up an error message saying "This workbook cannot be saved in the selected file format because it contains multiple sheets." In this instance, that's not an issue and you can click "OK."

#### Current Cue Sheet Version: 1.1.0

## Getting Started

For each track in your library, fill out a row with "Filename" and then populate the ensuing rows with the metadata for that track. The filename should only be added to the first row for each track. The following rows should leave filename blank. [See below](#columns) for a description of each column.

In addition to filling out the primary metadata, you can add rules that can modify the title, link, and/or usage based on time in the sequence. This allows you to, for example, set the usage of a theme song to MT for main title early in a sequence and ET for end title late in the sequence. See Rules for more information.

## Columns

- Filename - The filename of the track. Filename is case sensitive, file extension must be included.
- Title - Title of the track
- Link - If you have a link to a specific track online, you can include the link here. Q-Cuts will add a hyperlink in the final cue sheet (if that setting is enabled)
- Mix ID - If you have multiple versions of a track, for example, one with vocals and one without, include the filename of the main mix in this column for all alternate mixes (leave the column blank for the main mix). If Q-Cuts sees simultaneous or sequential tracks that are different mixes of the same master, it will merge them together into a single cue taking the metadata of the master mix. See the Mix IDs section below for more details.
- Usage - Required for RapidCue cue sheets, you must characterize how the track is being used. Must be one of:
    - Logo
    - MT = Main Title Theme
    - ET = End Title Theme
    - VV = Visual Vocal
    - VI = Visual Instrumental
    - BV = Background Vocal
    - BI = Background Instrumental

With the following fields, you fill in the composer and publisher credits. There must be only one credit per line and a line cannot contain both a composer/arranger and a publisher.

- Role - One of: Composer, Publisher, or Arranger
- Composer or Arranger (First and Middle Name) - First and middle name of composer or arranger
- Composer or Arranger (Last Name) - Last name of composer or arranger
- Publisher - Name of song publisher
- PRO Affiliation - If the composer, arranger, or publisher has a Performance Rights Organization (PRO) affiliation, add it to this column. Examples include ASCAP or BMI.
- Shares - Percent of shares each credited artist is entitled to. Shares is optional, but should be a number between 0 and 100. All shares for a track should add up to 100

The following columns allow you to set time rules that alter the metadata for a clip. For example, setting a different usage after a certain time. Before and After measure sequence runtime, not timecode, and are checked against the start time of the clip. Rules can be used to alter one or more of the following properties: Title, Link, Usage. Mix ID and Composer/Arranger/Publisher credits cannot be modified using rules.

- After HH
- After MM
- After SS
- Before HH
- Before MM
- Before SS

For example, if you have a track that serves as both the opening and closing credits for a television program and you want to report its usage as as 'MT' if it's in the first ten minutes of the program and 'ET' for any subsequent use, you can do something like this:

| Filename      	| Title      	| Link                         	| Mix ID 	| Usage 	| Role      	| Composer or Arranger (First and   Middle Name) 	| Composer or Arranger (Last Name) 	| Publisher                 	| PRO Affiliation 	| Shares 	| After HH 	| After MM 	| After SS 	| Before HH 	| Before MM 	| Before SS 	|
|---------------	|------------	|------------------------------	|--------	|-------	|-----------	|------------------------------------------------	|----------------------------------	|---------------------------	|-----------------	|--------	|----------	|----------	|----------	|-----------	|-----------	|-----------	|
| ThemeSong.wav 	| Theme Song 	| [https://hans-zimmer.com/news](https://hans-zimmer.com/news) 	|        	| MT    	| Composer  	| Hans                                           	| Zimmer                           	|                           	| ASCAP           	| 50     	|          	|          	|          	|           	|           	|           	|
|               	|            	|                              	|        	|       	| Publisher 	|                                                	|                                  	| Downtown Music Publishing 	|                 	| 50     	|          	|          	|          	|           	|           	|           	|
|               	|            	|                              	|        	| ET    	|           	|                                                	|                                  	|                           	|                 	|        	| 0        	| 10        	| 0        	|           	|           	|           	|


## Basic CSV

Here is a basic CSV example. This is how you might enter a track called "GreatSong.wav" in your CSV.

| Filename                   | Title                             | Link                                                                                       | Mix ID        | Usage | Role      | Composer or Arranger (First and Middle Name) | Composer or Arranger (Last Name) | Publisher                  | PRO Affiliation | Shares | After HH | After MM | After SS | Before HH | Before MM | Before SS |
| -------------------------- | --------------------------------- | ------------------------------------------------------------------------------------------ | ------------- | ----- | --------- | -------------------------------------------- | -------------------------------- | -------------------------- | --------------- | ------ | -------- | -------- | -------- | --------- | --------- | --------- |
| GreatSong.wav              | Great Song                        | [https://www.youtube.com/watch?v=dQw4w9WgXcQ](https://www.youtube.com/watch?v=dQw4w9WgXcQ) |               | BV    | Composer  | Joe                                          | Smith                            |                            | ASCAP           | 40     |          |          |          |           |           |           |
|                            |                                   |                                                                                            |               |       | Arranger  | Sarah                                        | Brown                            |                            | BMI             | 10     |          |          |          |           |           |           |
|                            |                                   |                                                                                            |               |       | Publisher |                                              |                                  | Universal Music Publishing |                 | 50     |          |          |          |           |           |           |

Note that the filename is only on the first line of metadata for the track and then additional credits or metadata are filled in on subsequent lines.

## CSV with Mix ID

 In this slightly more advanced example, we add an instrumental version of GreatSong.wav and we'll use the Mix ID column to tell Q-Cuts that the two tracks are linked. Note that we only fill in the Mix ID column for the alternative mix, not for the primary mix.

| Filename                   | Title                             | Link                                                                                       | Mix ID        | Usage | Role      | Composer or Arranger (First and Middle Name) | Composer or Arranger (Last Name) | Publisher                  | PRO Affiliation | Shares | After HH | After MM | After SS | Before HH | Before MM | Before SS |
| -------------------------- | --------------------------------- | ------------------------------------------------------------------------------------------ | ------------- | ----- | --------- | -------------------------------------------- | -------------------------------- | -------------------------- | --------------- | ------ | -------- | -------- | -------- | --------- | --------- | --------- |
| GreatSong.wav              | Great Song                        | [https://www.youtube.com/watch?v=dQw4w9WgXcQ](https://www.youtube.com/watch?v=dQw4w9WgXcQ) |               | BV    | Composer  | Joe                                          | Smith                            |                            | ASCAP           | 40     |          |          |          |           |           |           |
|                            |                                   |                                                                                            |               |       | Arranger  | Sarah                                        | Brown                            |                            | BMI             | 10     |          |          |          |           |           |           |
|                            |                                   |                                                                                            |               |       | Publisher |                                              |                                  | Universal Music Publishing |                 | 50     |          |          |          |           |           |           |
| GreatSong-Instrumental.wav | Great Song - Instrumental Version | [https://www.youtube.com/watch?v=8leAAwMIigI](https://www.youtube.com/watch?v=8leAAwMIigI) | GreatSong.wav | BI    | Composer  | Joe                                          | Smith                            |                            | ASCAP           | 40     |          |          |          |           |           |           |
|                            |                                   |                                                                                            |               |       | Arranger  | Sarah                                        | Brown                            |                            | BMI             | 10     |          |          |          |           |           |           |
|                            |                                   |                                                                                            |               |       | Publisher |                                              |                                  | Universal Music Publishing |                 | 50     |          |          |          |           |           |           |