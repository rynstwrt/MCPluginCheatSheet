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
##6. Permissions
  1. Create the permission in the main class
    * `Permission canBuild = new Permission("myplugin.canbuild");`
  2. Check if player has a permission
    * `if (plr.hasPermission("myplugin.canbuild")) {}`

##7. Configuration Options (config.yml)
  1. Generate (if not already present) (put in onEnable() function)
    * `this.getConfig().addDefault("playervisits", 0)`
  2. Keep config as default
    * `this.getConfig().options().copyDefaults(true);`
  3. Save the config (put in onDisable() too)
    * `saveConfig();`
  4. How to get data
    * `firstclass.getConfig().getInt("playervisits");`
  5. How to set data
    * `firstclass.getConfig().set("playervisits", configGetter.getConfig().getInt("playervisits") + 1);`
  6. Check if something exists in the config
    * `if (firstclass.getConfig().contains("playervisits.player1") {}`
  7. Sections
    * Referenced as `this.getConfig().getInt("playervisits.player1");`
    * Set as `plugin.getConfig().set("playervisits.player2", 200);`
  8. Multiple Configs
    * Use `FileConfig x = YamlConfiguration.loadConfiguration(new File(plugin.getDataFolder(), "example.yml"));`
```yaml
  playervisits:
    player1: 10
    player2: 100
    player3: 1337 
``` 

##8. Scheduler
  1. Set up `Bukkit.getScheduler().scheduleSyncRepeatingTask(this, new Runnable(<run function>) {}, startupTimeInTicksL, repeatingTimeInTicksL`
  2. Times are in ticks (20 ticks = 1 second)
  3. Use `scheduleSyncRepeatingTask` for loops, and `scheduleSyncDelayedTask` for waits (like cooldowns)
  4. In total, a countdown will look like this:
```Java
if (cmd.getName().equalsIgnoreCase("count3")) {
				num = 3;
				Bukkit.getScheduler().scheduleSyncRepeatingTask(this, new Runnable() {
					@Override
					public void run() {
						if (num > 0) {
							Bukkit.broadcastMessage("" + num);
						} else if (num == 0) {
							Bukkit.broadcastMessage("Go!");
						}	
            num--;
					}		
				}, 0L, 1*20L);	
				return true;
			}
```
