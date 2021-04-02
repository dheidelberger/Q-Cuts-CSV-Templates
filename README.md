# Q-Cuts CSV Template files

Use these template files to add CSV filters to the Q-Cuts cue sheet generation extension for Adobe Premiere.

Because of some of the formatting that's built in to the .xlsx template, it is highly recommended that you work in that version of the template in Excel and then save it as a CSV for import into Q-Cuts

#### Current Version: 1.1.0

## Getting Started

For each track in your library, fill out a row with "Filename" and then populate the ensuing rows with the metadata for that track. The filename should only be added to the first row for each track. The following rows should leave filename blank. [See below](#columns) for a description of each column.

In addition to filling out the primary metadata, you can add rules that can modify the title, link, and/or usage based on time in the sequence. This allows you to, for example, set the usage of a theme song to MT for main title early in a sequence and ET for end title late in the sequence. See Rules for more information.

More documentation and a full CSV tutorial can be found online

## Columns

- Filename - The filename of the track. Filename is case sensitive, file extension must be included.
- Title - Title of the track
- Link - If you have a link to a specific track online, you can include the link here. Q-Cuts will add a hyperlink in the final cue sheet (if that setting is enabled)
- Mix ID - If you have multiple versions of a track, for example, one with vocals and one without, include the filename of the main mix in this column for all alternate mixes (leave the column blank for the main mix). If Q-Cuts sees simultaneous or sequential tracks that are different mixes of the same master, it will merge them together into a single cue taking the metadata of the master mix. See the Mix IDs section below for more details.
- Usage - Required for RapidCue cue sheets, you must characterize how the track is being used. Must be one of: BI = Background Instrumental, BV = Background Vocal, VI = Visual Instrumental, VV = Visual Vocal, MT = Main Title Theme, ET = End Title Theme, Logo

With the following fields, you fill in the composer and publisher credits. There must be only one credit per line and a line cannot contain both a composer/arranger and a publisher.

- Role - One of Composer, Publisher, or Arranger
- Composer or Arranger (First and Middle Name) - First and middle name of composer or arranger
- Composer or Arranger (Last Name) - Last name of composer or arranger
- Publisher - Name of song publisher
- PRO Affiliation - If the composer, arranger, or publisher has a Performance Rights Organization (PRO) affiliation, add it to this column. Examples include ASCAP or BMI.
- Shares - Percent of shares each credited artist is entitled to. Shares is optional, but should be a number between 0 and 100. All shares for a file should add up to 100

The following columns allow you to set time rules that alter the metadata for a clip. After and Before allow you to assign special rules for a file. For example, setting a different usage after a certain time. Before and After measure runtime, not timecode, and are checked against the start time of the clip

- After HH
- After MM
- After SS
- Before HH
- Before MM
- Before SS
