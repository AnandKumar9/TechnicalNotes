Create a new object whose instances can be made -

function Point(x, y) {
  this.x = x;
  this.y = y;
}     

Point.prototype.distance = function() {
  return Math.sqrt(this.x * this.x + this.y * this.y);
};                              // Add a function to an object

var p = new Point(3, 5);        // Create a new instance of the object


Create an unnamed object -

var jane = {
  name: 'Jeremy',
  describe: function() {
    return 'Person named ' + this.name;
  }
};


Function definition -

function func1(a, b) {
  return a + b;
}

Treating function like some data -

var f = function(a, b) {
  return a + b;
};
