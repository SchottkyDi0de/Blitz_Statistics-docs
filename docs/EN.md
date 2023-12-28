# **Command Syntax**:

### `/command [arg_1] <arg_2> <arg_3>`
- Some commands have arguments that can be required or optional. > `/command [arg]`
- If an argument is specified in square brackets `[]`, it is **required**
- If an argument is specified in angle brackets `<>`, it is **optional**

> `[arg_name] <arg_name>`

***Example:***

### `/parse_replay [replay] [region] <output_type>`

- The **`replay`** argument is required.
- The **`output_type`** argument is optional, so it can be omitted.


# **Configuration Commands:**
### 1: `/set_lang [lang]`

***Arguments:***
- **`lang`** List of available languages (string)

***What it does:***
- Sets the localization language of the bot for you.

> 📝 **_Note:_** The `default` language includes automatic language selection.
Automatic selection is based on the language set in your Discord application interface.

---
### 2: `/set_player [nickname] [region]`
***Arguments:***
- `nickname` Player nickname for saving (string)
- `region` Region for search (string)

***What it does:***
- Records the player in the database for future use, for example for the **`/astats`** command.


# **Statistics Retrieval Commands:**
### 1: `/stats [nickname] [region]`
***Arguments:***

- `nickname` Player nickname for search (string)
- `region` Region for search (string)

***What it does:***

- Searches for a player with the specified nickname in the specified region.
If the player is found, an image with detailed statistics is returned.
Otherwise, an error is returned.
---
### 2: `/astats`

***What it does:***

- Same as **`/stats`**, but no input is required, as the data is taken from the database after registering with the **`/set_player`** command.


# **Game Session Management Commands:**
### 1: `/start_session`

***What it does:***
- Starts a session, after starting the session, you need to play several battles to generate the session.

> **_Note:_** To use, you need to save your data using **`/set_player`**

---
### 2: `/get_session`

***What it does:***

- Generates a player session and sends an image with session statistics in response.

> **_Note:_** To use, save your data with the **`/set_player`** command and start the session with the **`/start_session`** command.

---
### 3: `/session_state`

***What it does:***

- Displays whether the session is active and the time the session is active.

# **Commands for managing user backgrounds:**

### 1: `/set_background [image] <server> <resize_mode>`
***Arguments:***
- `image` Image file (700x1350), with the following restrictions:
 -- Formats: `PNG`, `JPEG`
 -- Size of one side should not exceed 2048 px and should not be less than 256 px
 -- File size should not be more than 2MB
- `server` If `True`, the image is applied as the default image for the server where the command was invoked. Administrator permissions on the server are required.
- `resize_mode` Method of resizing the image (if it's not 700x1350)
 -- `AUTO`: Automatically determines the best method for resizing
 -- `RESIZE`: Resizes the image ignoring proportions, applied automatically when the deviation from the nominal size is less than `10%` in X and `15%` in Y
 -- `CROP_OR_FILL`: Crops the image and centers it if it is larger than necessary or centers it and adds a filler in the form of blurred parts of the original image if the size of the image is smaller than necessary. Does not violate the proportions of the image. Applied automatically if the deviations in size exceed the permissible values.

***What it does:***
 - Saves the submitted image as the background for images with statistics.
 > 📝 **Note:** 
 > - We are not responsible for the image you upload to the bot. It is not processed or checked in any way. If the uploaded image violates Discord rules, your account may be blocked and you will lose access to the commands of this app.
 > - Server administrators can disable the ability to use custom images, and when requesting statistics, you will see either the default background or the background set as the default on this server.
 ---
 ### 2: `/image_settings <args>`
 ***Arguments:***
 - `use_custom_bg`: `bool` - Ability to use a custom background (True by default)
 - `glass_effect`: `int` - Blur parameter for the background behind the blocks with statistics in the image. 0 - Disables blurring.
 - `blocks_bg_brightness`: `int` - Brightness of the background behind the blocks with statistics (in %)
 - `nickname_color`: `str` - Nickname color in [HEX Color code](https://www.color-hex.com) format. Example: `#ff0000` - red
 - `clan_tag_color`: `str` - Clan tag color
 - `stats_color`: `str` - Color of the main statistics digits, such as the number of battles in the account.
 - `main_text_color`: Color of the main text, such as the statistics category
 - `stats_text_color`: Color of the statistics labels such as `average damage` or `rating`, which are located below the main statistics.
 - `disable_flag`: `bool` - Disables the region flag in the image
 - `hide_nickanme`: `bool` - Hides the nickname. If enabled, the nickname is changed to `Player`
 - `hide_clan_tag`: `bool` - Hides the clan tag in the statistics. If enabled, the clan tag is not displayed.
 - `disable_stats_blocks`: Disables the rendering of contrasting blocks that highlight the statistics on the background image. Can be useful if you have prepared your own background image and the standard highlighting of the statistics interferes.
 - `disable_rating_stats`: Disables the display of the block with rating statistics when requesting session statistics.
 
 ***What it does:***
 - Saves and applies the set image settings.
 
 > 📝 **Note:** All arguments of this command are optional. Change as many settings as you deem necessary, untouched settings will not be changed.
 ---
 ### 3: [`/image_settings_get`](#image_settings_get)
 ***What it does:***
 - Sends the user their current image settings.
 > 📝 **Note:** Explanation of some parameters: 
 > `True` - yes or true, `False` - no or false

---
# **Commands for managing server settings:**

### 1: `/server_settings <args>`
***Arguments:***
- `allow_user_backgrounds`: Parameter that determines whether users are allowed to use their own backgrounds for statistics on this server.

***What it does:***
- If `True`, it replaces the user's image with the default image set for this server or with a standard image if a default background is not set on the server.

---

### 2: `/server_settings_get`
***What it does:***
- Displays the current server settings to the user, just like [`/image_settings_get`](#image_settings_get)
# **Other Commands:**

### 1: `/parse_replay [replay] [region] <output_type>`

***Arguments:***
- `replay` Replay file with the extension **`.wotbreplay`**
- `region` Region in which the battle was played

***What it does:***

- Shows basic information about the replay, a list of battle participants from the replay, and their statistics.

---
### 2: `/ping`

***What it does:***

- Displays the bot's response time.

> 📝 **_Note:_** This command is currently disabled for improvement.
