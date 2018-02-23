# Proyecto-Juego
/********* VARIABLES GLOBALES *********/
int gameScreen;
int turn;
int hp1, hp2;

class personaje {
  // Atributos 
  String name; 
  int hp;
  int attack;
  int defense;
    
  // Parámetros del método de consturcción de clase.
  personaje(String name_, int hp_, int attack_, int defense_){
    
    // Parámetros del método de construcción se asignan como valores de atributos.
    name = name_;
    hp = hp_;
    attack = attack_;
    defense = defense_;
        
  }
}

personaje Batman1;
personaje Spiderman1;
personaje KickAss1;
personaje Saitama1;
personaje Supervaca1;
personaje NewGuy1;

personaje Batman2;
personaje Spiderman2;
personaje KickAss2;
personaje Saitama2;
personaje Supervaca2;
personaje NewGuy2;
  
// Player 1, 2.

personaje player1;
personaje player2;

//Turno para seleccionar.
int ts = 0;

boolean player1Selection = false;
boolean player2Selection = false;

color cBatman = color(255,0,0), cSpiderman = color(0,255,0), cKickAss = color(0,0,255), cSaitama = color(255,0,255), cSupervaca = color(0,255,255), cNewGuy = color(255,255,0);

/********* SETUP BLOCK *********/

void setup() {
  size(800, 600);
  background(255);
  
  // Personajes jugador 1.
  Batman1 = new personaje("Batman", 60, 20, 10);
  Spiderman1 = new personaje("Spiderman", 50, 15, 15); 
  KickAss1 = new personaje("Kick-Ass", 80, 10, 10);
  Saitama1 = new personaje("Saitama", 50, 10000, 20);
  Supervaca1 = new personaje("Supervaca", 60, 25, 10);
  NewGuy1 = new personaje("New Guy", 45, 25, 20);
  
  // Personajes jugador 2.
  Batman2 = new personaje("Batman", 60, 20, 10);
  Spiderman2 = new personaje("Spiderman", 50, 15, 15); 
  KickAss2 = new personaje("Kick-Ass", 80, 10, 10);
  Saitama2 = new personaje("Saitama", 50, 10000, 20);
  Supervaca2 = new personaje("Supervaca", 60, 25, 10);
  NewGuy2 = new personaje("New Guy", 45, 25, 20);
}

/********* DRAW BLOCK *********/

void draw() {
  // Display the contents of the current screen.
  switch (gameScreen) {
    case 0:
      iniScreen();
    break;
    case 1:
      stScreen();
    break;
    case 2:
      charScreen();
    break;
    case 3:
      figScreen();
    break;
    case 4:
      vicScreen();
    break;
  }
}

/********* PANTALLAS *********/

// 0: Initial Screen                  (iniScreen)
// 1: Story Screen                    (stScreen)
// 2: Character Selection Screen      (charScreen)                     
// 3: Fighting Screen                 (FigScreen)
// 4: Victory Screen                  (VicScreen) 

void iniScreen() {
  // Código de pantalla de inicio.
  background(0);
  textAlign(CENTER, CENTER);
  text("SAVE THE EARTH 1,2,3,4,5,6...",400,200);
  text("Haz click para iniciar", 400, 300);
  
  if (mousePressed) {
    gameScreen = 1;
  }

}
void stScreen() {
  // Código de pantalla de historia.
  background(255);
  fill(0);
  textAlign(CENTER, CENTER);
  text("6 universos distintos colapsan uno sobre el otro y depende de cada héroe salvar el suyo\n ¿A quién ayudarás?",400,200);
  text("Presiona una tecla para continuar", 400, 300);
  
  if (keyPressed) {
    gameScreen = 2;
  }

}
void charScreen() {
  // Código de pantalla de selección de personajes.
  background(255);
  noStroke();
  fill(cBatman);
  ellipse(131,150,30,30);
  fill(cSpiderman);
  ellipse(400,150,30,30);
  fill(cKickAss);
  ellipse(666,150,30,30);
  fill(cSaitama);
  ellipse(131,450,30,30);
  fill(cSupervaca);
  ellipse(400,450,30,30);
  fill(cNewGuy);
  ellipse(666,450,30,30);
  
  fill(0);
  
  //INSTRUCCIONES
  pushMatrix();
  text("Selecciona a tú HÉROE haciendo click",300,570);
  popMatrix();
  
   //ATRIBUTOS
   fill(0);
   
   //BATMAN
   
  textAlign(LEFT);
  text("HP:  60",220,100);
  text("ATA:  20",220,120);
  text("DEF:  10",220,140);

   
   //SPIDERMAN
   
  textAlign(LEFT);
  text("HP:  50",480,100);
  text("ATA:  15",480,120);
  text("DEF:  15",480,140);
  
   //KICK-ASS
   
  textAlign(LEFT);
  text("HP:  80",730,100);
  text("ATA:  10",730,120);
  text("DEF:  10",730,140);
  
  //SAITAMA
   
  textAlign(LEFT);
  text("HP:  50",220,400);
  text("ATA:  ?",220,420);
  text("DEF:  20",220,440);
  
  //SUPERVACA
   
  textAlign(LEFT);
  text("HP:  60",480,400);
  text("ATA:  25",480,420);
  text("DEF:  10",480,440);
  
  //NEW GUY
   
  textAlign(LEFT);
  text("HP:  45",740,400);
  text("ATA:  25",740,420);
  text("DEF:  20",740,440);
  
    
  pushMatrix();
  translate(-50,0);
  BATMAN();
  popMatrix();
  
  pushMatrix();
  translate(200,0);
  SPIDERMAN();
  popMatrix();
  
  pushMatrix();
  translate(450,0);
  KICKASS();
  popMatrix();
  
  pushMatrix();
  translate(-50,280);
  SAITAMA();
  popMatrix();
  
  pushMatrix();
  translate(200,280);
  SUPERVACA();
  popMatrix();
  
  pushMatrix();
  translate(450,280);
  NEWGUY();
  popMatrix();
  
  if (player1Selection && player2Selection){
      
    gameScreen = 3;
    turn =+1;
  }
          
}

void figScreen() {
  // Código de pantalla de lucha. 
  background (255);
  println(player1.name, hp1);
  println(player2.name, hp2);
  
  pushMatrix();
  text("TURNO:"+turn,90,80);
  popMatrix();
  
  
  
  
  //Barra de vida Player1
    pushMatrix();
    noStroke();
    fill(350,0,0);
    rectMode(CORNER);
    rect(135,100,hp1,30);
    noFill();
    popMatrix();
    
    //Barra de vida Player2
    pushMatrix();
    fill(255,0,0);
    rect(500,100,hp2,30);
    noFill();
    popMatrix();
    
    //Instrucciones
    
    fill(0);
    text("Jugador 1 presiona 'Q' para atacar",135,450);
    text("Jugador 2 presiona 'P' para atacar",500,450);
    
    
  
  //Visualización de personaje.
  
  //Jugador1
  
   pushMatrix();
    translate(25, 150);
    if (player1 == Batman1){
      
      BATMAN();
    }
    else if (player1 == Spiderman1){
      
      SPIDERMAN();
    } 
    else if (player1 == KickAss1){
      
      KICKASS();
    } 
    else if (player1 == Saitama1){
      
      SAITAMA();
    } 
    else if (player1 == Supervaca1){
      
      SUPERVACA();
    } 
    else if (player1 == NewGuy1){
      NEWGUY();
    }
    popMatrix();
    
  
    
    //Jugador2
    
    pushMatrix();
    translate(375, 150);
    if (player2 == Batman2){
      
      BATMAN();
    }
    else if (player2 == Spiderman2){
      
      SPIDERMAN();
    } 
    else if (player2 == KickAss2){
      
      KICKASS();
    } 
    else if (player2 == Saitama2){
      
      SAITAMA();
    } 
    else if (player2 == Supervaca2){
      
      SUPERVACA();
    } 
    else if (player2 == NewGuy2){
      NEWGUY();
    }
    popMatrix();
    
    
    
    

  switch (turn){
    case 1:
  keyPressed();
      if ((key == 'Q') || (key == 'q')){
        hp2 = hp2 - (player1.attack - (player2.defense/2));
        println(player1.name, hp1);
        turn = 2;
      }
      break;
      
      case 2:
  keyPressed();
      if ((key == 'P') || (key == 'p')){
        hp1 = hp1 - (player2.attack - (player1.defense/2));
        println(player1.name, hp1);
        turn = 1;
      }
      break;
          
  }
  if(hp1 <= 0 || hp2 <=0){
    gameScreen = 4;
  }

  //Código alternativo de lucha.
  
  /*turn = 1;      
  
        
    if (turn == 1){
      
      keyPressed();
      if ((key == 'Q') || (key == 'q')){
        hp2 =- player1.attack;
        println(player1.name, hp1);
        turn = 2;
      }
      else if (turn == 2){
         keyPressed();
         if ((key == 'P') || (key == 'p')){
            hp1 =- player2.attack;
            println(player2.name, hp2);
            turn = 1;
         }
      }
          
  }*/
  
}
void vicScreen() {
  // Código de pantalla de victoria.
  background(0);
  
  textAlign(CENTER, CENTER);
  fill(255);
  
  if (hp1 > 0){
    text("Victoria Jugador 1 " + player1.name, 400, 200);
  }
  else if(hp2 > 0){
    text("Victoria Jugador 2 " + player2.name, 400, 200);
  }
  
  text("Haz click para seleccionar personaje", 400, 300);
  if (mousePressed){
    gameScreen = 2;
    player1Selection = false;
    player2Selection = false;
    ts = 0;
    turn = 0;
   
  }
   
}

/********* INPUTS *********/
void mousePressed (){
  
  if (gameScreen == 2) {
      
     if ((mouseX> 0) && (mouseX< 267) && (mouseY> 0) && (mouseY< 300)){
        //println("mouse sobre Batman");
        if (ts == 0){
          player1 = Batman1;
          hp1 = player1.hp;
          player1Selection = true;
          ts = 1;
          println("Player 1 elige a Batman");           
        }
        else if (ts == 1){
          player2 = Batman2;
          hp2 = player2.hp;
          player2Selection = true;
          println("Player 2 elige a Batman");
           
         }
         cBatman = color(random(255),random(255),random(255)); 
     }
                       
     if( (mouseX> 267) && (mouseX< 533) && (mouseY> 0) && (mouseY< 300)){
        //println("mouse sobre Spiderman");
        if (ts == 0){
          player1 = Spiderman1;
          hp1 = player1.hp;
          player1Selection = true;
          ts = 1;
          println("Player 1 elige a Spiderman");
        }
        else if (ts == 1){
          player2 = Spiderman2;
          hp2 = player2.hp;
          player2Selection = true;
          println("Player 2 elige a Spiderman");
    
        }
        cSpiderman = color(random(255),random(255),random(255));
     }
           
     if( (mouseX> 533) && (mouseX< 800) && (mouseY> 0) && (mouseY< 300)){
        //println("mouse sobre Kick-Ass");
        if (ts == 0){
          player1 = KickAss1;
          hp1 = player1.hp;
          player1Selection = true;
          ts = 1;
          println("Player 1 elige a Kick-Ass");
        }
        else if (ts == 1){
          player2 = KickAss2;
          hp2 = player2.hp;
          player2Selection = true;
          println("Player 2 elige a Kick-Ass");
          
        }
        cKickAss = color(random(255),random(255),random(255)); 
     }
                         
     if( (mouseX> 0) && (mouseX< 267) && (mouseY> 300) && (mouseY< 600)){
        //println("mouse sobre Saitama");
        if (ts == 0){
          player1 = Saitama1;
          hp1 = player1.hp;
          player1Selection = true;
          ts = 1;
          println("Player 1 elige a Saitama");
        }
        else if (ts == 1){
          player2 = Saitama2;
          hp2 = player2.hp;
          player2Selection = true;
          println("Player 2 elige a Saitama");
          
        }
        cSaitama = color(random(255),random(255),random(255));
      }
        
     if( (mouseX> 267) && (mouseX< 533) && (mouseY> 300) && (mouseY< 600)){
        //println("mouse sobre Supervaca");
        if (ts == 0){
          player1 = Supervaca1;
          hp1 = player1.hp;
          player1Selection = true;
          ts = 1;
          println("Player 1 elige a Supervaca");
        }
        else if (ts == 1){
          player2 = Supervaca2;
          hp2 = player2.hp;
          player2Selection = true;
          println("Player 2 elige a Supervaca");
          
        }
        cSupervaca = color(random(255),random(255),random(255));
      }
             
     if( (mouseX> 533) && (mouseX< 800) && (mouseY> 300) && (mouseY< 600)){
        //println("mouse sobre New Guy");
        if (ts == 0){
          player1 = NewGuy1;
          hp1 = player1.hp;
          player1Selection = true;
          ts = 1;
          println("Player 1 elige a New Guy");
        }
        else if (ts == 1){
          player2 = NewGuy2;
          hp2 = player2.hp;
          player2Selection = true;
          println("Player 2 elige a New Guy");
        }
        cNewGuy = color(random(255),random(255),random(255));
      } 
  }
}

/********* OTHER FUNCTIONS *********/

void BATMAN(){

  pushMatrix();
  translate(0,0);
  noStroke();
    
  //BATMAN
  
  //Busto
  fill(0);
  ellipseMode(RADIUS);
  arc(200,190,80,70,radians(10),radians(170));
  
  //Máscara
  fill(40);
  rectMode(CENTER);
  rect(200,150,100,100);
  triangle(150,75,150,100,170,100);
  triangle(250,75,230,100,250,100);
  triangle(200,92,170,100,230,100);
  rectMode(CORNER);
  rect(150,200,100,15);
  
  //Ojos
  fill(255);
  triangle(170,132,195,135,175,145);
  triangle(230,132,225,145,205,135);
  
  //Piel
  rectMode(CENTER);
  //fill(#F7E3E3);
  fill(#FCDEDE);
  rect(200,185,80,50);
  fill(40);
  triangle(160,160,190,160,160,166);
  triangle(240,160,210,160,240,166);
  
  //Boca
  stroke(1);
  strokeWeight(2);
  line(190,180,230,180);
 
  popMatrix();
}

void SPIDERMAN(){
  
  pushMatrix();
  translate(0,0);
  noStroke();
  
  //SPIDERMAN
  
  //Busto
  fill(#F50A0A);
  ellipseMode(RADIUS);
  arc(200,190,80,70,radians(20), radians(160));
  
  //Máscara
  //fill(#FF3636);
  fill(#F52323);
  stroke(1);
  strokeWeight(1);
  triangle(140,150,160,91,160,200);
  triangle(260,150,240,93,240,200);
  noStroke();
  ellipseMode(RADIUS);
  ellipse(200,150,55,85);
  stroke(1);
  line(140,150,260,150);
  noStroke();
   
  //Red
  noFill();
  stroke(1);
  strokeWeight(1);
  ellipseMode(RADIUS);
  //arc(200,150,55,85,radians(0),radians(20),PIE);
  arc(200,150,55,85,radians(20),radians(40),PIE);
  arc(200,150,55,85,radians(40),radians(60),PIE);
  arc(200,150,55,85,radians(60),radians(80),PIE);
  arc(200,150,55,85,radians(80),radians(100),PIE);
  arc(200,150,55,85,radians(100),radians(120),PIE);
  arc(200,150,55,85,radians(120),radians(140),PIE);
  arc(200,150,55,85,radians(140),radians(160),PIE);
  //arc(200,150,55,85,radians(160),radians(180),PIE);
  //arc(200,150,55,85,radians(180),radians(200),PIE);
  arc(200,150,55,85,radians(200),radians(220),PIE);
  arc(200,150,55,85,radians(220),radians(240),PIE);
  arc(200,150,55,85,radians(240),radians(260),PIE);
  arc(200,150,55,85,radians(260),radians(280),PIE);
  arc(200,150,55,85,radians(280),radians(300),PIE);
  arc(200,150,55,85,radians(300),radians(320),PIE);
  arc(200,150,55,85,radians(320),radians(340),PIE);
  //arc(200,150,55,85,radians(340),radians(360),PIE);
   
  //Ojos
  stroke(1);
  strokeWeight(3);
  fill(255);
  triangle(145,112,195,150,155,175);
  triangle(255,112,245,175,205,150);
  
   popMatrix();
}

void KICKASS(){
  
  pushMatrix();
  translate(0,0);
  noStroke();
  
   
  //KICK-ASS
  
  //Busto
  fill(#0B3615);
  ellipseMode(RADIUS);
  arc(200,190,80,70,radians(10),radians(170));
  
  //Máscara
  fill(#11501F);
  triangle(140,150,160,91,160,200);
  triangle(260,150,240,93,240,200);
  noStroke();
  ellipseMode(RADIUS);
  ellipse(200,150,55,85);
  noFill();
  strokeWeight(4);
  stroke(#F7EE34);
  rectMode(CENTER);
  rect(200,172,40,15,7);
  noStroke();
  fill(#F7EE34);
  triangle(180,70,180,140,168,110);
  triangle(190,65,190,140,195,100);
  triangle(220,70,220,140,232,110);
  triangle(210,65,210,140,205,100);
    
  //Piel
  fill(#F2B962);
  strokeWeight(4);
  stroke(#F7EE34);
  rectMode(CENTER);
  rect(200,150,80,30,7);
  noStroke();
  rect(200,200,40,20,7);
  
  //Ojos
  fill(255);
  triangle(180,142,170,152,190,152);
  triangle(220,142,210,152,230,152);
  fill(0);
  triangle(180,142,180,152,190,152);
  triangle(220,142,220,152,230,152);
  
  //Boca
  stroke(1);
  strokeWeight(2);
  line(190,200,215,200);
  line(215,200,217,198);
      
  popMatrix();
}

void SAITAMA(){
  
  pushMatrix();
  translate(0,0);
  noStroke();
  
  //SAITAMA
  
  //Busto
  fill(#F2B518);
  ellipseMode(RADIUS);
  arc(200, 190, 80, 70, radians(30), radians(150));
  fill(#EADFCE);
  arc(200, 190, 80, 70, radians(30), radians(50));
  arc(200, 190, 80, 70, radians(130), radians(150));
  
  //Cara
  fill(#FFD89D);
  strokeWeight(1);
  triangle(140,150,160,91,160,200);
  triangle(260,150,240,93,240,200);
  ellipseMode(RADIUS);
  ellipse(200,150,55,85);
  
  //Ojos
  fill(255);
  ellipseMode(RADIUS);
  arc(180,142,10,10,radians(10),radians(170));
  arc(220,142,10,10,radians(10),radians(170));
  fill(0);
  ellipse(180,146,2,2);
  ellipse(220,146,2,2);
  stroke(0);
  strokeWeight(2);
  line(170,137,187,137);
  line(213,137,230,137);
  
  //Boca
  stroke(0);
  strokeWeight(2);
  line(194,200,206,200);
  
  //Nariz
  strokeWeight(1);
  line(200,150,198,180);
    
  popMatrix();
}

void SUPERVACA(){
  
  pushMatrix();
  translate(0,0);
  noStroke();
   
  //SUPERVACA
  
  //Busto
  fill(#CB0ACB);
  ellipseMode(RADIUS);
  arc(200,190,80,70,radians(10),radians(170));
  fill(#45BF25);
  arc(200,190,80,70,radians(10),radians(30));
  arc(200,190,80,70,radians(150),radians(170));
  
  
  //Cara
  fill(#936115);
  rectMode(CENTER);
  rect(180,80,30,30,10);
  rect(220,80,30,30,10);
  fill(#FAE09F);
  ellipseMode(RADIUS);
  triangle(180,80,120,100,180,100);
  triangle(220,80,220,100,280,100);
  
  ellipse(200,150,55,85);
  fill(#FAE09F);
  ellipse(200,170,70,65);
  fill(#FF9DFE);
  ellipse(230,170,30,40);
  ellipse(160,160,23,20);
  
  //Ojos
  fill(255);
  ellipseMode(RADIUS);
  arc(190,100,10,15,radians(0),radians(180));
  arc(210,100,10,15,radians(0),radians(180));
  fill(0);
  ellipse(193,106,3,4);
  ellipse(207,106,3,4);
  stroke(0);
  strokeWeight(2);
  line(178,98,200,100);
  line(200,100,222,98);
    
  popMatrix();
}

void NEWGUY(){
  
   pushMatrix();
  translate(0,0);
  noStroke();
  
  //NEW GUY
  
  //Busto
  fill(#F2B518);
  ellipseMode(RADIUS);
  arc(200, 190, 80, 70, radians(30), radians(150));
  fill(#EADFCE);
  arc(200, 190, 80, 70, radians(30), radians(50));
  arc(200, 190, 80, 70, radians(130), radians(150));
  
  //Cara
  fill(#936115);
  rectMode(CENTER);
  rect(136,95,30,30,10);
  rect(264,95,30,30,10);
  fill(#FFD89D);
  ellipseMode(RADIUS);
  ellipse(200,150,85,85);
  fill(#FAF8F5);
  ellipse(200,150,85,65);
  fill(#ACDFFA);
  ellipse(200,150,50,50);
  fill(0);
  ellipse(200,150,30,30);
  fill(255);
  ellipse(220,135,12,12);
  
  popMatrix();
}
  
