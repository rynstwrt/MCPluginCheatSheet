# MCPluginCheatSheet

##1. Naming Conventions
..* Package Name: websiteending/me.name/websiteurl.projectname
..* Class Name: ProjectNameCamelCase.java

##2. Initial Functions
####All must be below a @Overide metadata
..* `public void onEnable() {}`
..* `public void onDisable() {}`
..* `public boolean onCommand(CommandSender sender, Command cmd, String label, String[] args) {return false;}`

##3. Event Class
..* Implement the listener class: `public class <classname> implements Listener {}`
..* Start with constructor: `public <classname>(<firsclass> plugin) {plugin.getServer().getPluginManager().registerEvents(this, plugin)}`
 
