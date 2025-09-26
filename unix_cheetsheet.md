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
