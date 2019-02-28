##### The official docs for call() say: The call() method calls a function with a given this value and arguments provided individually.

##### What that means, is that we can call any function, and explicitly specify what this should reference within the calling function. Really similar to the bind() method! This can definitely save us from writing hacky code (even though we are all still hackerzzz).

- The main differences between bind() and call() is that the call() method:
  ⋅⋅\* Accepts additional parameters as well,
  ⋅⋅\* Executes the function it was called upon right away.
  ⋅⋅\* The call() method does not make a copy of the function it is being called on.
  ⋅⋅\* call() and apply() serve the exact same purpose. The only difference between how they work is that call() expects all parameters to be passed in individually, whereas apply() expects an array of all of our parameters. Example:

```javascript
var pokemon = {
  firstname: 'Pika',
  lastname: 'Chu ',
  getPokeName: function() {
    var fullname = this.firstname + ' ' + this.lastname;
    return fullname;
  },
};

var pokemonName = function(snack, hobby) {
  console.log(this.getPokeName() + ' loves ' + snack + ' and ' + hobby);
};

pokemonName.call(pokemon, 'sushi', 'algorithms'); // Pika Chu loves sushi and algorithms
pokemonName.apply(pokemon, ['sushi', 'algorithms']); // Pika Chu loves sushi and algorithms
```
