# IMGD5010_InstructBubbles
## Instructions
1. Create canvas to be full size of window.
1. Create multiple circles with slight offsets from each other to create a sketch like appearance.
1. Create a small highlight circle placed in the top left of the larger circles
1. Create an even smaller highlight circle to be placed on the top left edge of the larger highlight circle.
1. Randomize the placement of the circles across the canvas.
1. Randomize the coloring of the circles to switch between green, blue, and purple.

## Inspiration/Goal
My design is inspired not only by the look of bubbles but also the colors that tend to reflect from them. My goal was to make a piece of art that looks like it is light, airy, and has movement even though it is static. 


## Code
```
let bubbles = [];
let numBubbles = 50; // Number of bubbles to draw

function setup() {
  createCanvas(windowWidth, windowHeight);
  noFill();
  noLoop();
  
  // Generate random bubbles with random sizes and positions
  for (let i = 0; i < numBubbles; i++) {
    let size = random(20, 100); // Random size between 20 and 100
    let x = random(width); // Random X position
    let y = random(height); // Random Y position
    bubbles.push(new SketchBubble(x, y, size));
  }
}

function draw() {
  background('#fefaf7'); 
  // Display all the bubbles
  for (let bubble of bubbles) {
    bubble.display();
  }
}

// SketchBubble class to create the hand-drawn effect
class SketchBubble {
  constructor(x, y, size) {
    this.x = x;
    this.y = y;
    this.size = size;

    // Randomly assign an outline color
    this.colors = ['#473198', '#9BF3F0', '#74D9A8']; 
    this.outlineColor = random(this.colors); // Pick a random color from the list
    // this.highlightColor = random(this.colors)
  }

  display() {
    stroke(this.outlineColor); // Set the outline color to the random one
    strokeWeight(1);
    noFill(); // No fill for the circles
    
    // Draw multiple slightly offset ellipses to create a sketch effect
    for (let i = 0; i < 5; i++) {
      let offsetX = random(-2, 2); // Random horizontal offset
      let offsetY = random(-2, 2); // Random vertical offset
      let randomSize = this.size + random(-5, 5); // Slightly randomize size each time
      ellipse(this.x + offsetX, this.y + offsetY, randomSize, randomSize);
    }

    // Add highlights
    this.addHighlights();
  }

  addHighlights() {
    stroke(this.outlineColor);
    strokeWeight(1);
    
    // Larger highlight
    let highlightSize = this.size * 0.3;
    ellipse(this.x - this.size * 0.2, this.y - this.size * 0.2, highlightSize, highlightSize);
    
    // Smaller highlight
    highlightSize = this.size * 0.1;
    ellipse(this.x - this.size * 0.3, this.y - this.size * 0.3, highlightSize, highlightSize);
  }
}
```
Link to p5.js code: https://editor.p5js.org/JessilynCollette/sketches/E9ZgshMrm
