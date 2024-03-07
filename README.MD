# About the reloading plugin for Minecraft

A plugin for automatically reloading PaperMC and BungeeCord plugins as their classes are recompiled. Forked of the Jrebel plugin.

# Installation of developpement environement

Setting the plugin up is simple, simply place the JAR for the plugin you are using in a location
you will remember and update your startup arguments.

#### For BungeeCord

```bash
-Drebel.plugins=path/to/bungee-rebel-plugin.jar -Drebel.bungee=true
```

#### For PaperMC
```bash
-Drebel.plugins=path/to/bukkit-rebel-plugin.jar -Drebel.bukkit=true
```

If done correctly you should see the following message appear in stdout, though obviously the timestamp will be different.

```
2016-02-12 13:21:02 JRebel: Plugins will be reloaded when class changes are detected.
```

Now you simply compile classes like normal and wait for JRebel to reload them, when a reload occurs
then the plugin you installed will kick in and attempt to reload any PaperMC or Bungee plugins that use
the reloaded class.

## Recommendation

As far as I'm aware it is not possible to reload shaded dependencies using JRebel, for this reason I advise you to
use Gradle's `distribution` plugin or Maven's dependency plugin (`org.apache.maven.plugins:maven-dependency-plugin`)
plugin to copy dependency JARs into the classpath prior to launching the server with JRebel. Once you finish writing
your code you can enable dependency shading once more for a pain-free experience.

# License

```
Copyright (C) 2016 Connor Spencer Harries

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
