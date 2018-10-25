# DIse-o-Generativo
float paso = TWO_PI/40;
float alto = 1;
float radioX = 80;
float radioY = 80;
PVector centro = new PVector(0,0);
float delta, delta2;
void setup(){
  size(400,400,P3D);
  sphereDetail(4);
  delta = random(-1, 1);
  delta2 = random(-5, 5);
}
 void draw(){
  /*if (mousePressed){
  delta+=0.05;
  }*/
  lights();
  background(255);
  translate(100,400,-400);
  pushMatrix();
  rotateX(-mouseY*0.02);
  rotateY(-mouseX*0.002);
  noStroke();
  fill(255,0,0);
  
  for (int j = 0; j<200; j+=alto){
    pushMatrix();
    rotate(j);
    for(float i = 0; i<TWO_PI; i+=paso){
      float px = centro.x + cos(i)*(j*0.9+sin(.8+j*0.02)*40);
      float py = centro.y+ sin(i)*(j*0.9+sin(.8+j*0.02)*40);
      float pz = j;
      pushMatrix();
      translate(px,py,pz);
      sphere(15);
      popMatrix();
    }  
    popMatrix();
  }
  
  for (int j = 0; j<500; j+=alto){
    pushMatrix();
    rotateX(50);
    rotateY(20);
    rotate(j);
    for(float i = 0; i<TWO_PI; i+=paso){
      float px = centro.x + cos(i)*sin(delta)+(radioX-60);
      float py = centro.y + sin(i)*(radioY-60);
      float pz = j;
      pushMatrix();
      translate(px,py,pz);
      sphere(10);
      popMatrix();
    }  
    popMatrix();
  }
  popMatrix();
}

void mousePressed() {  
  saveFrame("I###.jpg");
  }
