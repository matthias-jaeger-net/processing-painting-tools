# processing-painting-tools

## Toolset of methods to painterly draw within a processing sketch
[Processing](https://processing.org/) is a flexible software sketchbook and a language for learning how to code within the context of the visual arts. I base my toolset on this creative collection of methods and try to extend them to fit the needs of painters, illustrators and graphic designers.

## A sidenote to myself (maybe useful to you)
This is one one of countless attemps to organize my creative coding and collect what I already know. While attempting creative coding projects you can easily get distracted and work in crazy directions, producing non-reusable programs full of hard coded elements. Here I will try to be strict to myself and write simple functions doing one thing only. Can I even do that? We will find out, because I havent written any code yet. Starting out with the readme first seems a good thing. 

## The format of a painting defines your processing sketch...
Format relates to the size and shape of a painting.  If it is a rectangle, the orientation can be longer in the vertical dimension (portrait) - or longer in the horizontal (landscape).  Format decisions  on both size and shape of the art surface will impact the composition and the effects. For now I imagine this basic sketch:

```java
void setup() {
  // A landscape format given inside of setup()
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

This is a perfecty fine sketch, but i would want to store the width and height of my processing canvas in variables. If you want to do that you can use the ``settings()``function. Tryig tho call ``size()``with variables inside of ``setup()``will create an error. Is this a good method I dont know? I want to create an artwork like so: ``Artwork a = new Artwork(w, h)`` and also want the sketch to get the format from there.

```java
class Artwork {
  public int Width, Height; 
  Artwork(int[] f) { setFormat(f); } 
  void setFormat(int[] f) {
    Width  = f[0];
    Height = f[1];
  }
  int getFormatWidth() { return Width; }
  int getFormatHeight() { return Width; }
  void render() {
    background(255);
    line(100, 100, 200, 180);
  }
}
final int[] format = {700, 500};
Artwork artwork = new Artwork(format);
void settings() { size(artwork.Width, artwork.Height); }
void setup() { noLoop(); }
void draw() { artwork.render(); }

```
## Replacing the line function with the idea of a brush stroke
Thinking about the second parameter of the canvas, because this has grown in code a lot and does the same thing as in the basic sketch. I begin on thinking of the second parameter of a canvas the color of it's surface, leaving out the texture for now. I cleared up the code and start working on the first hard thing: Replacing the line function with the idea of a brush stroke.

```java
class Artwork {
  private int CanvasWidth, CanvasHeight, CanvasColor;
  Artwork(int[] f, int c) { 
    setCanvasWidth(f[0]); 
    setCanvasHeight(f[1]); 
    setCanvasColor(c);
  } 
  void setCanvasWidth(int w)  { CanvasWidth  = w; }
  void setCanvasHeight(int h) { CanvasHeight = h; }
  void setCanvasColor(int c)  { CanvasColor = c; }
  int  getCanvasWidth()       { return CanvasWidth; }
  int  getCanvasHeight()      { return CanvasHeight; }
  int  getCanvasColor()       { return CanvasColor; }
  void renderCanvasColor()    { background(CanvasColor); }
  void renderLine()           { line(100, 100, 200, 180); }
  void render()               { renderCanvasColor(); renderLine(); }
}
Artwork artwork = new Artwork(new int[]{700, 500}, 255);
void settings() { size(artwork.getCanvasWidth(), artwork.getCanvasHeight()); }
void setup() { noLoop(); }
void draw() { artwork.render(); }
```
