# mie

An experiment with creating declarative composable factories to stamp out objects.

```JS
var person = mie.factory('person').extend({
  walk: function() {
    console.log('walk');
  },
  talk: function() {
    console.log('talk');
  }
});

var stealthy = mie.factory('stealthy').extend({
  sneak: function() {
    console.log('sneak');
  }
});

var solider = mie.factory('solider').is('person').extend({
  march: function() {
    console.log('march');
  },
  shoot: function() {
    console.log('shoot');
  }
});

var sniper = mie.factory('sniper').is('solider', 'stealthy').extend({
  march: function() {
    console.log('march');
  },
  shoot: function() {
    console.log('shoot');
  }
});

var danny = person.create('danny', {
  fname: 'Danny',
  lname: 'Blue'
});

var aaron = solider.create('aaron', {
  fname: 'Aaron',
  lname: 'Druck'
});

var cody = sniper.create('cody', {
  fname: 'Cody',
  lname: 'Henthorne'
});

person.list(); // {danny: {...}, aaron: {...}, cody: {...}}
soldier.list(); // {aaron: {...}, cody: {...}}
sniper.list(); // {cody: {...}}

mie.factory('person').get('cody') // returns cody
mie.factory('soldier').get('danny') // returns undefined

```
