# CSC106-FinalProject
This is a repository to work on our group project for our CSC106 class
noStroke();
var t = 0;// time
var y = 0;// how high the ball is, where 0 is on the ground

var ball = function(x,y,h){
    this.x=200;
    this.y=200;
    this.h=40;
};
ball.prototype.draw= function() {
    y = -0.04*t*t + 4.0*t;// y follows the path of a parabola with respect to t!
    // since y is a positive height, we need to flip it
    // to look right on the inverted coordinate plane
    var newY = 341 - 1.5*y;
    fill(71, 117, 255);
    ellipse(this.x, newY, this.h, this.h);
};
ball.prototype.control=function(){
   if (keyIsPressed && keyCode === LEFT) {
       this.x-=2;
   }
   if (keyIsPressed && keyCode === RIGHT) {
       this.x+=2;
   }
};
var Ball=new ball();

var draw = function() {
    background(255, 255, 255);
    Ball.draw();
    Ball.control();
    if (y < 0) { // if y becomes negative, the ball has hit the ground
        t = 0;// reset t to make it "bounce" up again
    }
    t += 2.5; //how fast ball is moving 
};
