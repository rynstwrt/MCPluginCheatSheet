# MCPluginCheatSheet

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
    usage: /ping
```
  
 

##4. Event Class
 * Implement the listener class: `public class <listenerclassname> implements Listener {}`
 * Start with constructor: `public <listenerclassname>(<firsclass> plugin) {plugin.getServer().getPluginManager().registerEvents(this, plugin)}`
 * Events are then implemented under a @EventHandler metadata tag as `public void <functionName>(<eventHere> e) {}`
