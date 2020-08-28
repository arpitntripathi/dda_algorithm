window.onload = function(){
    var canvas = document.querySelector('#canvas');
    var width = window.innerWidth;
    var height = window.innerHeight;
    
    var ctx = canvas.getContext("2d");
    
    canvas.width = width;
    canvas.height = height;
    
    var x, y, x0, y0, x1, y1, dx, dy, steps, xIncr, yIncr;
    
    x0 = parseInt(prompt("Enter value for x1", 150));
    y0 = parseInt(prompt("Enter value for y1", 150));
    x1 = parseInt(prompt("Enter value for x2", 300));
    y1 = parseInt(prompt("Enter value for y2", 300));
    
    dx = x1 - x0;
    dy = y1 - y0;
    
    if(dx > dy){
        steps = Math.abs(dx);
    }else{
        steps = Math.abs(dy);
    }
    
    xIncr = dx / steps;
    yIncr = dy / steps;
    
    
    
    var i = 1;
    x = x0;
    y = y0;
    
    var time = setInterval(draw, 25);
    
    
    
    function draw(){
        if(i <= steps){
            putPixel(x, y);
            x = x + xIncr;
            y = y + yIncr;
            
        }else{
            clearInterval(time);
        }
        i++;
    }
 
    function putPixel(x, y){
        ctx.beginPath();
        ctx.arc(x, y, 1, 0, Math.PI * 2, false);
        ctx.fillStyle = "rgba(225,225,225,0.7)";
        ctx.fill();
        ctx.closePath();    
    }
    
}