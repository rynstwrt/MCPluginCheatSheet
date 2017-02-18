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
 1. name: ProjectName
 2. main: packagename.FirstClass
 3. version: X.X
 4. author: YourUsername
 5. commands:
  +commandname:
   1.description: Simulates a pingpong match
   2.usage: `/<command>`
 

##4. Event Class
 * Implement the listener class: `public class <listenerclassname> implements Listener {}`
 * Start with constructor: `public <listenerclassname>(<firsclass> plugin) {plugin.getServer().getPluginManager().registerEvents(this, plugin)}`
 * Events are then implemented under a @EventHandler metadata tag as `public void <functionName>(<eventHere> e) {}`
