# Metadata-Transfer

The `Metadata.py` script is a Python application with a Tkinter GUI designed to transfer metadata from audio files to corresponding MP4 video files. It helps users keep their video files organized and correctly tagged by leveraging existing metadata from their audio library.

## Core Functionality

- **GUI Interface:** Utilizes `tkinter` to offer a user-friendly graphical interface. This allows users to easily select directories and monitor the progress and logs of the metadata transfer process.
- **Directory Selection:** Enables users to specify two key directories:
    - A folder containing the MP4 video files that need metadata.
    - A root folder for their audio library, which the script will search for matching audio files.
- **Filename Parsing:** For each MP4 video file, the script attempts to parse its filename to extract the artist and song title. It primarily assumes a common naming convention like "Artist - Song Title.mp4".
- **Audio File Matching:** After parsing the MP4 filename, the script searches the provided audio library for a corresponding audio file. This search is based on matching the extracted artist and title metadata. The script supports a variety of common audio file formats (e.g., MP3, FLAC, M4A).
- **Metadata Transfer:** Upon finding a matching audio file, the script uses the `mutagen` library to read a comprehensive set of metadata tags from the audio file. These tags can include artist, title, album, genre, year, track number, disc number, compilation status, composer, and comments. This extracted metadata is then written to the corresponding MP4 video file.
- **Logging:** Provides real-time logging information directly within the GUI. This log includes details about which files are being processed, whether audio matches were found, any errors encountered during the process, and a summary upon completion.
- **Error Handling:** Incorporates error handling to manage various potential issues. This includes gracefully handling unparseable MP4 filenames, situations where no matching audio file is found, problems encountered while reading metadata from audio files or writing it to video files, and errors related to file or directory access.

## How to Use

1.  **Running the Script:**
    *   Open a terminal or command prompt.
    *   Navigate to the directory where you saved `Metadata.py`.
    *   Run the script using Python: `python Metadata.py` or `python3 Metadata.py`.

2.  **Using the GUI:**
    *   **Video Folder:** Click the "Browse..." button next to "MP4 Video Folder" to open a dialog. Navigate to and select the folder that contains your `.mp4` video files.
    *   **Audio Library Folder:** Click the "Browse..." button next to "Audio Library Folder" to open a dialog. Navigate to and select the root folder of your music library. The script will search this folder and its subdirectories for matching audio files.
    *   **Starting Processing:** Once both folders are selected, click the "Start Processing" button. The script will begin to scan your video files, search for matching audio, and transfer metadata.
    *   **Log Output:** The text area at the bottom of the window will display real-time updates. This includes:
        *   The video file currently being processed.
        *   Whether a matching audio file was found.
        *   Confirmation of successful metadata transfers.
        *   Any errors or warnings encountered (e.g., file not found, metadata read/write issues).
        *   A summary of operations upon completion.
        Check this log area for details on the process.

## Dependencies

1.  **Python 3:**
    *   The script is written for Python 3. Ensure you have Python 3 installed on your system.

2.  **Libraries:**
    *   **`tkinter`**:
        *   This library is used for the Graphical User Interface (GUI).
        *   It is part of the Python standard library, so a separate installation is typically not required.
    *   **`mutagen`**:
        *   This library is used for reading and writing audio metadata.
        *   You will likely need to install it. You can do this using pip:
            ```bash
            pip install mutagen
            ```

## File Structure

*   `Metadata.py`: The main Python script containing the application logic and GUI.
*   `README.md`: This file.

## Features

*   **Graphical User Interface (GUI):** Easy-to-use interface for selecting directories and monitoring progress.
*   **MP4 Metadata Tagging:** Transfers a comprehensive set of metadata tags from audio files to MP4 video files.
*   **Flexible Audio File Matching:** Identifies matching audio files based on artist and title parsed from video filenames.
*   **Support for Various Audio Formats:** Works with common audio file types (MP3, FLAC, M4A, AAC, OGG, etc.) via the `mutagen` library.
*   **Detailed Logging:** Provides real-time feedback on operations, successes, and errors within the GUI.
*   **Configurable Audio Extensions:** The list of recognized audio file extensions (`AUDIO_EXTENSIONS`) is defined in the script and can be modified.
*   **Error Handling:** Gracefully handles common issues such as filename parsing failures, missing audio matches, and metadata processing errors.

## Known Limitations/Future Improvements

**Known Limitations:**

*   **Filename Parsing:** Currently relies on a specific filename format (`Artist - Title.mp4`). Files not matching this pattern won't have their artist/title correctly parsed for matching.
*   **Metadata Overwriting:** If the MP4 file already has metadata, the script will overwrite existing values for the tags it's programmed to transfer. It doesn't clear all pre-existing tags but updates specific ones based on the audio file.

**Future Improvements:**

*   **Configurable Filename Parsing:** Allow users to define custom regex patterns for parsing filenames.
*   **Advanced Metadata Options:**
    *   Option to choose which specific metadata tags to transfer.
    *   Option to explicitly preserve certain existing MP4 tags.
*   **Batch Editing/Dry Run:**
    *   Implement a "dry run" mode to allow users to preview potential changes before any metadata is actually written to the files.
*   **Cover Art Transfer:** Extend functionality to include transferring album art from audio to video files.
*   **More Robust Error Reporting:**
    *   Option to export the log to a file for easier review of errors and processed files.
