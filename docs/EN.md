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
