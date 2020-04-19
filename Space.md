### Space Shooter Using Artifical Intelligence

```javascript
var space = createSprite(200,200,800,800);
space.setAnimation("space1");

var player = createSprite(200,380,5,5);
player.setAnimation("hero");

player.scale = 0.1;
space.scale = 5;
var bullet;

var enemiesGroup = createGroup();
var bulletGroup = createGroup();

var score = 0;
function draw() {
  background("white");
  drawSprites();
  createEdgeSprites();
  fill("white");
  textSize(25);
  text("SCORE : "+score,250,50);

  space.velocityY = 2;
 // player.x= World.mouseX;
  
  if (space.y > 500) {
    space.y = space.height/2;
  }
  
  if(World.frameCount%50 === 0){
    var enemy = createSprite(randomNumber(50,350),0,20,20);
    enemy.setAnimation("enemies");
    enemy.velocityY = 5;
    enemy.scale = 0.3;
    enemiesGroup.add(enemy);
    player.x= enemy.x;
    Bullets();
  }
   
  for(var i=0;i<enemiesGroup.length;i++){

    if(bulletGroup.isTouching(enemiesGroup)){
     
      enemiesGroup.get(i).destroy();
      score++;
    }
  }
  
}
function Bullets(){
  
    bullet = createSprite(200,370,0,0);
    bullet.setAnimation("bulletS");
    bullet.scale=0.05;
    bullet.x=player.x;
    bullet.velocityY=-3;
    //bullet.debug = true;
    //bullet.setCollider("rectangle",0,0,200,200);
    bullet.depth=player.depth;
    player.depth = player.depth + 1;
    
    
    bulletGroup.add(bullet);
   
}
```



##### Code Output Link : 

[https://studio.code.org/projects/gamelab/O2373tKXXMo7-EZNEgfruCu-6b3-eQoLF0Zun7aMhK0]: 	"Code.org Link"



