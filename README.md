# ELAp5
function setup() {
  createCanvas(500, 500, WEBGL);
  angleMode(DEGREES)
}
const faces = [
  [0,   0, 0, '255, 0, 0'],
  [0,  90, 0, '0, 255, 0'],
  [0, 180, 0, '255, 0, 0'],
  [0, -90, 0, '0, 255, 0'],
  [90,  0, 0, '0, 0, 255'],
  [270, 0, 0, '0, 0, 255'],
  ];
const edgeLength = 135;
const explodeFactor = 1.3;
const animationFrames = 300;
const transparency = 0.6
  function draw() {
    const doneness = min(frameCount / animationFrames, 1);
    background(255, 170, 255);
  
    noStroke(1);
    rotateY(frameCount);
    rotateX(-frameCount);
    faces.forEach(face=> {
      fill( `rgba(${face[3]}, ${transparency})`);
           push();
      [rotateX, rotateY, rotateZ].forEach((fn, i) => 
        fn(face[i] * doneness)); 
      translate(0, 0, edgeLength / 2 * explodeFactor * doneness);
      plane(edgeLength);
      pop();
    });
  }
