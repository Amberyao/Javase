# Javase
具体思路如下: 
1.把控制台当做是一个直角坐标系，第一个点(0,0)为原点，这时控制台就相当于直角坐标系的第四象限，但我们要把它看成第一象限，因为这样不用涉及负数的问题. 
2.把（r，r）看成是圆的中心，如下图，先获取所要打印的*点的横坐标x，程序中调用getX(int r,int y)方法获取（利用直角三角形的勾股定理) 
![画圆](http://img.blog.csdn.net/20150606182743311)
3.先打印左边的空格，getSpace(int s)获取空格数，接着打印号 
4.接着打印两个号之间的空格，最后打印号，这样一行打印完成 
5.循环打印2 * r + 1次


package cycle;

import java.util.Scanner;

public class drawCycle {

	public static void main(String[] args) {
		System.out.println("请输入半径");
		Scanner in =new Scanner(System.in);//控制台获取信息
		int r=in.nextInt();
		paint(r);
	}
	public static void paint(int r){
		//假设圆心在（r,r）处，控制台起始点为（0，0）
		int x=0;//x坐标
		int y=0;//y坐标
		int c=0;//左右两个*之间的空格数
		int z=2;//用于控制纵横比，设为2刚刚好
		
		for(int i=0;i<=2*r;i+=2){
			//先获取每一行左边*号的左边X
			x=getX(r,y);
			//打印第一个*号之前的空格和*号
			System.out.print(getSpace(x)+"*");
			//打印两个*号之间的空格
			c=2*(r-x);
			System.out.println(getSpace(c)+"*");
			y+=2;
		}
	}
	public static int getX(int r,int y){
		//采用勾股定理，
		return (int)Math.round(r-Math.sqrt(r*r-(r-y)*(r-y)));
	}
	public static String getSpace(int c){
		String space=" ";
		for(int j=0;j<c;j++){
			space+=" ";
		}
		return space;
	}
}
