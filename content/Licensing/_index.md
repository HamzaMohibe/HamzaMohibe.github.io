+++
archetype = "chapter"
title = "Licensing"
weight = 4
+++
For the Apache 2 licence to apply to our code we need to have a text file containing the licence in the projects root and some boilerplate text in the header of each java file. To do this were using the plugin license-maven-plugin. 

## Explanation of code

![plugin](https://github.com/jrykns-org/not-a-virus-map/assets/55873910/53fd6a07-53e6-40f4-b9f3-9a8e3be308c1)

The plugin will load on each compile to check to see if the boiler plate text is in existing files, if its not it gets added automatically.
