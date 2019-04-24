# processing-painting-tools

## Toolset of methods to painterly draw within a processing sketch
[Processing](https://processing.org/) is a flexible software sketchbook and a language for learning how to code within the context of the visual arts. I base my toolset on this creative collection of methods and try to extend them to fit the needs of painters, illustrators and graphic designers.

## A sidenote to myself (maybe useful to you)
This is one one of countless attemps to organize my creative coding and collect what I already know. While attempting creative coding projects you can easily get distracted and work in crazy directions, producing non-reusable programs full of hard coded elements. Here I will try to be strict to myself and write simple functions doing one thing only. Can I even do that? We will find out, because I havent written any code yet. Starting out with the readme first seems a good thing. 

## The format of a painting
Format relates to the size and shape of a painting.  If it is a rectangle, the orientation can be longer in the vertical dimension (portrait) - or longer in the horizontal (landscape).  Format decisions  on both size and shape of the art surface will impact the composition and the effects. I store the width and the height of my processing canvas usually in two global variables For now I imagine this basic sketch:

```java
void setup() {
  // A landscape format
  size(700, 500);
  // No animation needed
  noLoop();
}
void draw() {
  // Clear the background with white
  background(255);
  // Here is my awsome grapic design
  line(100, 100, 200, 180);
}
```


// A landscape format
final int w = 700;
final int h = 500;
Toolset painter = new Toolset(w, h);

void settigs() { size(w, h); }
