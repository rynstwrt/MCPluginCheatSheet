#Minecraft Server Plugin Cheat Sheet <img src="https://hydra-media.cursecdn.com/minecraft.gamepedia.com/c/c5/Grass.png" width="42">

##1. Naming Conventions
 * Package Name: websiteending/me.name/websiteurl.projectname
 * Class Name: ProjectNameCamelCase.java

##2. Initial Functions
####All must be below a @Overide metadata tag
 * `public void onEnable() {}`
 * `public void onDisable() {}`
 * `public boolean onCommand(CommandSender sender, Command cmd, String label, String[] args) {return false;}`

##3. plugin.yml Configuration
```yaml
name: ProjectName
main: packagename.MainClass
version: 0.1
author: YourName
commands:
  ping:
    description: simulates a ping-pong game
    usage: /<command>
```
 
##4. Event Class
 * Start Listener (in first class) `onEnable() {new <listenerclassname>(this);}`
 * Implement the listener class: `public class <listenerclassname> implements Listener {}`
 * Start with constructor: `public <listenerclassname>(<firsclass> plugin) {plugin.getServer().getPluginManager().registerEvents(this, plugin)}`
 * Events are then implemented under a @EventHandler metadata tag as `public void <functionName>(<eventHere> e) {}`

##5. Command Arguments
  1. Check if arguments
    * `if (args.length == 1) {`
  2. Check if argument was a player (for this example)
```Java
      
      boolean plrFound = false;

      for (Player p : Bukkit.getServer().getOnlinePlayers()) {
        if (p.getName().equalsIgnoreCase(args[0])) {
          plrFound = true;
          p.setHealth(p.getMaxHealth());
          break;
        }
      }
      
      if (!plrFound) {
        plr.sendMessage("No player found!");
      }
```

##6. Configuration Options (config.yml)
  
