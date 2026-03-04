# Tracer

# Campus Lost and Found Discord Bot

This project is a Discord bot designed to manage a simple **lost and found system for communities such as campuses, clubs, or organizations**.
Users can upload images of found items, store contact details securely, search for items by name, and retrieve item information directly through Discord commands.

The bot running in a Python3 Virtual Environment stores item data in a **separate SQLite database for each Discord server**, ensuring that data from different servers does not mix.

Contact details are encrypted before being stored to protect user privacy.

---

# Features

### Item Upload

Users can upload an image of a found item along with its name. The bot assigns a unique item ID and stores the image locally.

### Secure Contact Storage

Finder and owner contact details are encrypted using Fernet encryption before being saved to the database.

### Item Search

Users can search for items by name using partial matching.

### Image Retrieval

The stored image of an item can be retrieved using the item ID.

### Per-Server Databases

Each Discord server automatically receives its own database file to keep records isolated.

### Item Descriptions

Users can optionally provide a description to help identify the item.

### Database Reset

Administrators can clear the entire database and remove stored images using a password-protected command.

---

# Commands

`!ping`
Checks whether the bot is online.

`!info`
Displays the list of available commands.

`!upload <item_name>`
Starts the upload process for a found item.
The bot will request:

* an image
* finder contact details
* an optional description

A unique item ID will be generated for reference.

`!find <item_name>`
Searches the database for items with names matching the provided text.

`!show-image <item_id>`
Displays the stored image associated with an item ID.

`!show-details <item_id>`
Reveals encrypted owner and finder contact details.

`!store-owner-details <item_name> <contact_details>`
Stores encrypted contact details for an item owner.

`!store-finder-details <item_id> <contact_details>`
Updates the finder contact details for an existing item.

`!clear_db <password>`
Deletes all records and stored images for the server.

---

# How the System Works

1. A user uploads an item using the upload command.
2. The bot saves the image inside a structured folder under the `uploads` directory.
3. The item metadata is stored in a SQLite database specific to the server.
4. Finder contact information is encrypted before storage.
5. When a user searches for an item, the bot queries the database and returns matching results.

Each item record contains:

* item ID
* item name
* encrypted owner details
* encrypted finder details
* description
* upload date
* path to stored image

---

# Installation

Clone the repository:

```
git clone https://github.com/yourusername/lost-found-bot.git
cd lost-found-bot
python3 -m venv venv
source venv/bin/activate
```

Install required dependencies:

```
pip install discord.py cryptography
```

---

# Configuration

Set your Discord bot token as an environment variable:

```
export DISCORD_BOT_TOKEN=your_token_here
```

Alternatively, you can replace the placeholder in the code.

---

# Running the Bot

Start the bot with:

```
python3 bot.py
```

If the token is valid and permissions are set correctly, the bot will connect to Discord and begin accepting commands.

---

# Security Notes

* Contact details are encrypted before being stored.
* Each server uses an independent database file.
* The database reset command requires a password.
* Uploaded images are stored locally on the host machine.

---

# Possible Improvements

Future development ideas include:

* automatic image similarity matching for lost items
* web dashboard for browsing items
* moderation controls for administrators
* cloud storage for images
* rate limiting to prevent spam uploads

---

# License

This project is intended for educational and experimental use.
You may modify and redistribute it as needed.
