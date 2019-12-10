<!Doctype html>
<html lang="en">
            <head>
            <meta charset="UTF-8">
            <title>Hello</title>
            <style type="text/css">
            canvas
            { border : 1px solid black;
             background : yellow;
            }
            </style>
            </head>
            <body>
            <canvas></canvas>
            <script>
            var canvas=document.querySelector('canvas');
            canvas.width=window.innerWidth;
            canvas.height=window.innerHeight;
            var c=canvas.getContext('2d');
            function Circle(x,y,dx,dy,radius)
            { this.x=x;
              this.y=y;
              this.dx=dx;
              this.dy=dy;
              this.radius=radius;
              this.draw=function()
              { c.beginPath();
                c.arc(this.x,this.y,this.radius,0,Math.PI*2,false);
                c.stroke();
                c.fillStyle='red';
                c.fill();
              }
              this.update= function()
              {  if(this.x+this.radius >innerWidth || this.x - this.radius < 0)
                  {this.dx=-this.dx;
                  }
                if(this.y+this.radius>innerHeight || this.y - this.radius < 0)
                {this.dy =-this.dy;
                }
                this.x=this.x+this.dx;
                this.y=this.y+this.dy;
                this.draw();
                
              }
               
            }
            var circleArray = [];
            for(var I=0;I<100;I++)
            {var radius= 30;
             var x= Math.random()*(window.innerHeight/1.1)+40;
             var y= Math.random()*(window.innerHeight/1.1)+40;
             var dx= Math.random()*10;
             var dy= Math.random()*9;
             circleArray.push(new Circle(x,y,dx,dy,radius));
            }
            function animate()
            { requestAnimationFrame(animate);
              c.clearRect(0,0,canvas.width,canvas.height);
             for(var I=0;I<circleArray.length;I++)
             {circleArray[I].update();
               }              
              circle.update();
            }
            animate();
            </script>
            </body> 
 </html>
