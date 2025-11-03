---
title: Adopting an orphan plugin 
description: Stepping forward to take care of an abandoned plugin
category: plugins
weight: 10
---

For a variety of reasons, plugins sometimes get abandoned by their creators. 
It could be that the original author has retired, moved on to other work, 
or sometimes even passed away. 

Community members with development and debugging skills are urged to consider picking up support for plugins that have been abandoned.  

Creating a Github repo for your contribution is nice but not required.  The advantage of doing this is that other people can submit PRs to fix bugs and enhance the operation of your plugin. 

It's good to include updated docs (or improve the docs if they're weak), and include a brief "changelog" in the docs to denote what was done "when" and what versions of Zen Cart and PHP the latest update is compatible with.

Useful references:
- [PHP version feature changes and deprecations](/dev/code/php_version_deprecations/)
- [Zen Cart requirements](/user/first_steps/server_requirements/#php-version)
- [Encapsulated Plugins](/dev/plugins/encapsulated_plugins/)


## Do's and Don'ts

- Do not remove anyone else's copyright or authorship claims.  You are welcome to add yourself, but don't take anything away. 
- Do not claim original authorship if you aren't the original author.  Make it clear that you're building on someone else's work.
- Make an effort to reach out to the original author to be sure the work has been abandoned.  It could be that the author just doesn't think more work is needed.
- Familiarize yourself with the [rules for plugins](/dev/plugins/rules/).
- Follow the [migration guides](/dev/plugins/php_updating/) to bring the plugin up to the current level of PHP.
- Whereever possible, try to use the [Observer/Notifier](/dev/code/notifiers/) system, rather than changing core files.  See the other [tips for plugin authors](/dev/plugins/tips/) as well.  
- When you have completed your work, submit the update as a new version to the Plugin Library. 

