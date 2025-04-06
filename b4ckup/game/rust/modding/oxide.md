# how to install a mod in rust server

## installing Oxide (uMod)

Navigate to the correct directory: On your server, navigate to the main Rust server directory (this will be rust_server if you've followed the steamcmd instructions without changing the name). Inside this directory, there is another directory named RustDedicated_Data. This is where the Oxide files need to be uploaded.

---

Before proceeding with this guide, ensure that you have Moderator or administrator permissions on your Rust server. If you are not already an admin or moderator on your server, you can grant yourself these permissions. Here are the steps to do this:

First, you need your Steam64ID. You can get this by going to a site like SteamID.io, entering your steam profile URL, and copying the steamID64.

Navigate to the users.cfg file. This will be in the same location as your server’s server.cfg file, which is in the /server/my_server_identity/cfg/ directory (replace my_server_identity with your server's identity).

Open users.cfg with a text editor, and add a new line in the following format: ownerid "YourSteamID64" "Your Name" "Optional Reason". Replace YourSteamID64 with your actual Steam64ID, Your Name with your actual username, and Optional Reason with the reason you’re adding this person as an admin (this can be anything and is not displayed in-game).

Save and close the file. Next time you start your server, you’ll be an admin! Alternatively, you can use the ownerid command in the server's console followed by the user’s Steam64ID, name, and optional reason.

---

## managing plugins

* ```oxide.version```: This command shows the version of Oxide being used on the server.

* ```oxide.reload PluginName:``` This command will unload and then load the specified plugin. This is useful when you have updated a plugin's configuration and need the changes to take effect.

* ```oxide.load PluginName```: This command will load the specified plugin if it's not already loaded.

* ```oxide.unload PluginName```: This command will unload the specified plugin.

In addition to plugin management, Oxide provides an additional permissions system for managing permissions on your server:

* ```oxide.group add "Group Name"```: This command creates a new group with the specified name.

* ```oxide.usergroup add "Username" "Group Name"```: This command adds the specified user to the specified group.

---

Each plugin can come with its own set of commands. For instance, if you have a plugin called "MyPlugin", it might have a command called "myplugin.mycommand". To allow a user to run this command, you would need to give them the necessary permission using the Oxide permissions system:

* ```oxide.grant user Username myplugin.mycommand```: This command gives the specified user permission to run the command myplugin.mycommand. Ensure you're familiar with your plugins' commands as they will help you configure and manage the plugin.

## Localization

Localization in the context of a Rust server powered by the Oxide plugin system refers to the process of customizing and translating various aspects of the server's interface and user interactions to match the languages and cultural preferences of your server's players.

## What are Language Files?

Language files are the backbone of the localization process in Oxide. They are text files that contain translations of various plugin texts and messages into different languages. Each plugin that supports localization will have its own set of language files, and each language supported by the plugin will have its own file. These files are usually in JSON format and can be easily edited to customize or add new translations.

### Where are language files located?

```
└── server
    └── rustserver
        └── oxide
            └── lang
                └── en
                    ├── SamplePlugin.json
                    └── AnotherPlugin.json
                └── es
                    ├── SamplePlugin.json
                    └── AnotherPlugin.json
```                    

### Modifying language files

Modifying a language file is straightforward and involves editing the respective JSON file using a text editor or an Integrated Development Environment (IDE) of your choice.

When you open the JSON file, you'll see a structure similar to the following:

```JSON
{
  "Hello": "Hello",
  "WelcomeMessage": "Welcome to our Rust server!"
}
```

```JSON
{
  "Hello": "Hello",
  "WelcomeMessage": "Welcome to our custom Rust server! Enjoy your stay."
}
```

Remember to save your changes before closing the file. The modified text will now be displayed when the corresponding event occurs in the game.

Different plugins may use different keys for their messages. Some plugins may also use placeholders (e.g., {0}, {1}, etc.) within their messages that are replaced with dynamic content when the message is displayed in the game. For instance, in a welcome message like below:

```JSON
{
  "WelcomeMessage": "Welcome to {0}! Enjoy your stay."
}
```