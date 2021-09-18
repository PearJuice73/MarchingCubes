ArrayList<PVector> points = new ArrayList<PVector>();

int x = 192 * 3;
int y = 108 * 3;
int spacing = 4;

OpenSimplexNoise noise;
OpenSimplexNoise noise2;
OpenSimplexNoise noise3;

void setup()
{
  background(55, 59, 56);
  
  noise = new OpenSimplexNoise(10);
  noise2 = new OpenSimplexNoise(15);
  noise3 = new OpenSimplexNoise(20);
  
  size(1920, 1080);
  strokeWeight(5);
  //randomSeed(5);
  
  
}

float zOff = 0;

void draw()
{
  background(39, 41, 39);
  
  float xOff = 0;
  float yOff = 0;
  zOff += 0.03;
  
  for (int i = 0; i < y * spacing; i += spacing)
  {
    yOff += .02;
    xOff = 0;
    for (int j = 0; j < x * spacing; j += spacing)
    {
      xOff += .01;
      
      float evaluatedColor = (float)(noise.eval(xOff, yOff, zOff)/* * (float)(noise2.eval(xOff, yOff, zOff)) *+ (float)(noise3.eval(xOff, yOff, zOff))*/);
      //\stroke(0,0,0,0);
      //fill((evaluatedColor + 1) * 255);
      
      evaluatedColor = ceil(evaluatedColor);
      //square(j, i, 10);
      
      //stroke((int)evaluatedColor * 255);
      points.add(new PVector(j, i, evaluatedColor));
    }
  }

  stroke(255);
  strokeWeight(2);

  for (int i = 0; i < (x - 1) * (y - 1); i ++)
  {
    int index = i;
    ArrayList<PVector> newArrayList = getSquare(index);
    int colors = getColorsOfSquare(newArrayList);

    drawLine(points.get(index), colors);
  }
  
  points.clear();
}

void drawLine(PVector point, int colors)
{
  if (colors == 13) //1101
  {
    line(point.x + spacing / 2, point.y + spacing, point.x, point.y + spacing / 2);
  }
  if (colors == 14) //1110
  {
    line(point.x + spacing / 2, point.y + spacing, point.x + spacing, point.y + spacing / 2);
  }
  if (colors == 12) //1100
  {
    line(point.x, point.y + spacing / 2, point.x + spacing, point.y + spacing / 2);
  }
  if (colors == 11) //1011
  {
    line(point.x + spacing / 2, point.y, point.x + spacing, point.y + spacing / 2);
  }
  if (colors == 9) //1001
  {
    line(point.x, point.y + spacing / 2, point.x + spacing / 2, point.y);
    line(point.x + spacing / 2, point.y + spacing, point.x + spacing, point.y + spacing / 2);
  }
  if (colors == 10) //1010
  {
    line(point.x + spacing / 2, point.y, point.x + spacing / 2, point.y + spacing);
  }
  if (colors == 8) //1000
  {
    line(point.x + spacing / 2, point.y, point.x, point.y + spacing / 2);
  }
  if (colors == 7) //0111
  {
    line(point.x + spacing / 2, point.y, point.x, point.y + spacing / 2);
  }
  if (colors == 5) //0101
  {
    line(point.x + spacing / 2, point.y, point.x + spacing / 2, point.y + spacing);
  }
  if (colors == 6) //0110
  {
    line(point.x + spacing / 2, point.y, point.x + spacing, point.y + spacing / 2);
    line(point.x, point.y + spacing / 2, point.x + spacing / 2, point.y + spacing);
  }
  if (colors == 5) //0101
  {
    line(point.x + spacing / 2, point.y, point.x + spacing / 2, point.y + spacing);
  }
  if (colors == 4) //0100
  {
    line(point.x + spacing / 2, point.y, point.x + spacing, point.y + spacing / 2);
  }
  if (colors == 3) //0011
  {
    line(point.x, point.y + spacing / 2, point.x + spacing, point.y + spacing / 2);
  }
  if (colors == 1) //0001
  {
    line(point.x + spacing / 2, point.y + spacing, point.x + spacing, point.y + spacing / 2);
  }
  if (colors == 2) //0010
  {
    line(point.x + spacing / 2, point.y + spacing, point.x, point.y + spacing / 2);
  }
}

int getColorsOfSquare(ArrayList<PVector> arrayList)
{
  String colors = "";
  if (arrayList.get(0).z == 0) colors += "0";
  else colors += "1";

  if (arrayList.get(1).z == 0) colors += "0";
  else colors += "1";

  if (arrayList.get(2).z == 0) colors += "0";
  else colors += "1";

  if (arrayList.get(3).z == 0) colors += "0";
  else colors += "1";

  return binaryToInt(colors);
}

int binaryToInt (String binary) {
  char []cA = binary.toCharArray();
  int result = 0;
  for (int i = cA.length-1; i>=0; i--) {
    //111 , length = 3, i = 2, 2^(3-3) + 2^(3-2)
    //                    0           1
    if (cA[i]=='1') result+=Math.pow(2, cA.length-i-1);
  }
  return result;
}

ArrayList<PVector> getSquare(int index)
{
  ArrayList<PVector> newArrayList = new ArrayList<PVector>();

  newArrayList.add(new PVector(points.get(index).x, points.get(index).y, points.get(index).z));
  newArrayList.add(new PVector(points.get(index + 1).x, points.get(index + 1).y, points.get(index + 1).z));
  newArrayList.add(new PVector(points.get(index + x).x, points.get(index + x).y, points.get(index + x).z));
  newArrayList.add(new PVector(points.get(index + x + 1).x, points.get(index + x + 1).y, points.get(index + x + 1).z));

  return newArrayList;
}
