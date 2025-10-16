# Unix Commands
## Create a new file
1. Create an empty file
touch filename          # Quick empty file
> filename              # Quick empty file or truncate existing

2. Create file with text
echo "Hello World" > filename       # Write text (overwrite)
echo "More text" >> filename        # Append text
printf "Line1\nLine2\n" > filename # Write formatted text

3. Interactive typing
cat > filename           # Type text, press Ctrl+D to save
nano filename            # Open nano editor
vi filename              # Open vi editor
vim filename             # Open vim editor


Quick guide to choose:
- Script/automation: touch, >, echo, printf
- Manual typing: cat
- Editing files: nano, vi, vim

## Nano editor
### File management
Open a file: nano filename.txt. If the file doesn't exist, nano will create it when you save.
Save a file: Press Ctrl + O.
Exit nano: Press Ctrl + X. If there are unsaved changes, you will be prompted to save before exiting. 
### Editing
Cut selected text or current line: Ctrl + K.
Copy selected text: Option + 6.
Paste text: Ctrl + U.
Search for text: Ctrl + W.
Search and replace: Ctrl + \.
Undo last action: Option + U.
Redo last undone action: Option + E. 
### Navigation
Go to the beginning of the line: Ctrl + A.
Go to the end of the line: Ctrl + E.
Page up: Ctrl + Y.
Page down: Ctrl + V.
Go to specific line: Ctrl + _, then enter the line number. 
### Help and settings
Display help menu: Ctrl + G.
Show cursor position: Ctrl + C. 

## move or rename folder (folder contents)
mv "source folder path" "target folder path"
