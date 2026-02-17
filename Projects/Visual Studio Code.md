From [Using Visual Studio Code for Theme Development](https://publish.obsidian.md/hub/04+-+Guides%2C+Workflows%2C+%26+Courses/Guides/Using+Visual+Studio+Code+for+Theme+Development) by [Damian Korcz](https://publish.obsidian.md/hub/01+-+Community/People/damiankorcz)

## Formatting

You can format using ⇧⌥F or **Format Document** from the context menu.

## Folding and Regions

Region Markers allow you to setup custom `Regions` which can help you with organising your code and as an additional way to fold your code.

**You can add custom Region Markers for CSS/Less/SCSS using:**

- `/*#region*/` at the Start of the Region.
- `/*#endregion*/` at the End of the Region.

**Fold All Regions Marker:**

`Ctrl+K` followed by `Ctrl+8` (Windows/Linux)  
`Cmd+K` followed by `Cmd+8` (MacOS)

**Unfold All Regions Marker:**

`Ctrl+K` followed by `Ctrl+9` (Windows/Linux)  
`Cmd+K` followed by `Cmd+9` (MacOS)

> 💡 **EXAMPLE**  
> ![VSCode Guide - Folding and Regions.gif](https://publish-01.obsidian.md/access/e25082da1bfe16d54e36618cd5bfee68/00%20-%20Contribute%20to%20the%20Obsidian%20Hub/02%20Attachments/VSCode%20Guide%20-%20Folding%20and%20Regions.gif)  
> You can organise different sections of your CSS/SCSS and make it easy to fold them away for easier navigation.

**More Info: [Folding and Regions](https://code.visualstudio.com/docs/editor/codebasics#_folding)**

### Search 

`Ctrl+Shift+F` (Windows/Linux)  
`Cmd+Shift+F` (MacOS)

> 💡 **EXAMPLE**  
> ![VSCode Guide - Search.gif](https://publish-01.obsidian.md/access/e25082da1bfe16d54e36618cd5bfee68/00%20-%20Contribute%20to%20the%20Obsidian%20Hub/02%20Attachments/VSCode%20Guide%20-%20Search.gif)  
> Search for a phrase across **all files in the Workspace**. You can replace that phrase with a new text. Click on any result to have it open up in the editor at the specific search result.

**More info: [Search](https://code.visualstudio.com/docs/editor/codebasics#_search-across-files)**

### Multiple Selection (multi-cursor) 

`Alt+Click` **OR** `Ctrl+Alt+Up` / `Ctrl+Alt+Down` (Windows/Linux)  
`Alt+Click` **OR** `Cmd+Alt+Up` / `Cmd+Alt+Down` (MacOS)

> 💡 **EXAMPLE**  
> ![VSCode Guide - Multiple Selection-Multi-Cursor.gif](https://publish-01.obsidian.md/access/e25082da1bfe16d54e36618cd5bfee68/00%20-%20Contribute%20to%20the%20Obsidian%20Hub/02%20Attachments/VSCode%20Guide%20-%20Multiple%20Selection-Multi-Cursor.gif)  
> Place the cursor where you click or add an additional one directly above or below the current one.

You can also `Click` to select a word, and press:

`Ctrl+D` (Windows/Linux)  
`Cmd+D` (MacOS)

This adds the next occurrence of the currently selected text to the selected text.

> 💡 **EXAMPLE**  
> ![VSCode Guide - Multiple Selection-Next-Occurrence.gif](https://publish-01.obsidian.md/access/e25082da1bfe16d54e36618cd5bfee68/00%20-%20Contribute%20to%20the%20Obsidian%20Hub/02%20Attachments/VSCode%20Guide%20-%20Multiple%20Selection-Next-Occurrence.gif)  
> You can quickly select the same word in your file without needing to individually place the next cursor by clicking. Handy when the word is in a different place on each line.

**More Info: [Multiple Selection (multi-cursor)](https://code.visualstudio.com/docs/editor/codebasics#_multiple-selections-multicursor)**

### Column (Box) Selection 

`Click` where you want to start a Column (Box) Selection, press and hold `Shift+Alt` while `Click` selecting to the opposite corner and release once the selection is complete. (Windows/Linux/MacOS)

> 💡 **EXAMPLE**  
> ![VSCode Guide - Column-Box Selection.gif](https://publish-01.obsidian.md/access/e25082da1bfe16d54e36618cd5bfee68/00%20-%20Contribute%20to%20the%20Obsidian%20Hub/02%20Attachments/VSCode%20Guide%20-%20Column-Box%20Selection.gif)  
> Use the Column (Box) Selection if you need to change some text/values that are horizontally aligned.

**More Info: [Column (Box) Selection](https://code.visualstudio.com/docs/editor/codebasics#_column-box-selection)**

### Toggle Wrapping in Current File 

`Alt+Z` (Windows/Linux/MacOS)

> 💡 **EXAMPLE**  
> ![VSCode Guide - Toggle Wrapping.gif](https://publish-01.obsidian.md/access/e25082da1bfe16d54e36618cd5bfee68/00%20-%20Contribute%20to%20the%20Obsidian%20Hub/02%20Attachments/VSCode%20Guide%20-%20Toggle%20Wrapping.gif)  
> If your file includes long lines of text e.g. Base64 embedded fonts/SVGs toggling Wrapping will make them remain on one line no matter the length or wrap the text around to the next line depending on the width of the File's window.

**More Info: [Toggle Wrapping in Current File](https://code.visualstudio.com/docs/editor/codebasics#_how-do-i-turn-on-word-wrap)**

### Go to Symbol

 **Go to Symbol** command (⇧⌘O).

### Rename Symbol 

Click on what you want to rename and press `F2` (Windows/Linux/MacOS)

> 💡 **EXAMPLE**  
> ![VSCode Guide - Rename Symbol.gif](https://publish-01.obsidian.md/access/e25082da1bfe16d54e36618cd5bfee68/00%20-%20Contribute%20to%20the%20Obsidian%20Hub/02%20Attachments/VSCode%20Guide%20-%20Rename%20Symbol.gif)  
> To rename any text/variable instances, click on one of them and press `F2`. Change the name to what you want and it will rename all of the instances of the selected text/variable to what you typed.

**More Info: [Rename Symbol](https://code.visualstudio.com/docs/editor/editingevolved#_rename-symbol)**

## Extensions
### Sass/SCSS 

- [**Sass**](https://marketplace.visualstudio.com/items?itemName=Syler.sass-indented) - Indented Sass syntax highlighting, autocomplete & Formatter for VSCode.
- [**SCSS IntelliSense**](https://marketplace.visualstudio.com/items?itemName=mrmlnc.vscode-scss) - SCSS IntelliSense (Variables, Mixins and Functions) for all files in the workspace.
- [**Stylelint**](https://marketplace.visualstudio.com/items?itemName=stylelint.vscode-stylelint) - A mighty, modern linter that helps you avoid errors and enforce conventions in your styles.