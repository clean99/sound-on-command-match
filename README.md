# sound-on-command-match
This repository contains a simple script that allows you to play a sound when a specific text is matched in the output of a command. This can be useful as an indicator or notification when running certain commands while you don't want to monitor the terminal.

## Prerequisites

Before using the script, ensure you have the following installed on your system:

- [grep](https://www.gnu.org/software/grep/)
- [aplay](https://linux.die.net/man/1/aplay) (Linux) or [afplay](https://ss64.com/osx/afplay.html) (macOS)

## How to Use

1. Create a file in the directory that you want to run the command:
    ```bash
    mkdir play_sound_on_match.sh
    # copy and paste the content from play_sound_on_match.sh
    ```

2. Grant permission to the script:
   ```bash
   chmod +x play_sound_on_match.sh
   ```
3. Edit the play_sound_on_match.sh script to set your desired command and specific text to match.
   ```bash
     #!/bin/bash
     # Command to run and monitor
     # replace the <> content
     <command you wanna run> | tee >(while IFS= read -r output; do
       if [[ $output == *"<string that you wanna match and play sound>"* ]]; then
        echo "Text matched: $output"
        afplay /System/Library/Sounds/Ping.aiff # for macOS. Linux please use aplay
        echo -e '\a'  # Play a system beep or sound
       fi
    done)
   ```

4. Run the script:
  ```bash
  ./play_sound_on_match.sh
  ```
5. When the specific text is matched in the command output, a sound will be played.

