Backbone.Streams
Author: Kevin "mrunderhill89" Cameron

A replacement event manager for Backbone.js, using Functional Reactive Programming from Bacon.js

Dependancies:
Backbone.js (http://backbonejs.org/)
Bacon.js    (https://github.com/baconjs/bacon.js)

General Idea:
Backbone.Streams replaces the existing event manager for Backbone.js with one that utilizes EventStreams from Bacon.js to make connecting events together much easier. Events are now handled through the "stream" method, which generates a new EventStream for the target object, or reuses existing streams as needed.

By default, each new stream is a Bacon.Bus, which means you can manually pass values into it, either through Bacon's Bus.push method, or through Backbone's trigger method (which now has a new alias, "fire").

For the most part, the API is explicitly designed so that you can use it the same way as Backbone's original event manager, only using the new stuff as needed. There is a slight catch in that passing multiple arguments to an event using trigger is no longer possible, since Bacon.Bus.push only seems to accept the first argument. You can always manually wrap your arguments in an array or object to get around this.

Usage:
The library structure is based off the one used for Backbone-Associations. I've tested it with require.js, but it should work fine with direct imports, as well. Just be sure this script is loaded after Backbone and Bacon. In addition, when using require.js, add this to your shims configuration:

backbone_streams:{
    deps:["backbone","bacon"],
    exports:"Backbone"
}
