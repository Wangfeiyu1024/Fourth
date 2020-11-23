# Fourth
第四次实验
# 计G201+2020322060+王菲钰  
# 实验名称   
## 模拟学生作业处理   
## 实验目的  
1.掌握字符串String及其方法的使用    
2.掌握文件的读取和写入的方法      
3.掌握异常的处理结构以及使用  
## 实验要求  

1.模拟学生提交实验结果，将该结果存储到文本文件A中。  
 * 文本文件A包含的内容：  
   学生的基本信息     
   学生处理后的作业信息   
   
2.处理作业内容（利用已学的字符串处理之事编程成《长恨歌》古诗的整理对齐工作 ）    
* 每7个汉字加入一个标点符号，奇数时加“，”，偶数时加“。”  
* 允许提供输入参数，统计古诗中某个字或词出现的次数  
* 输入的文本来源于文本文件B读取，把处理好的结果写入到文本文件A  
* 考虑操作中可能出现的异常，在程序中设计异常处理程序  

3.交互式实例化学生  
* 通过Scanner让用户输入学生信息，并使其信息直接写入文件中  
* 古诗处理完的结果存储到学生基本信息所在的文本文件A中  
## 实验过程  
  ### 1.建立包   
  * 在包中设置Info(信息）,Student(学生）    
  ### 2. Student类    
  * 方法：  
  1）Scanner输入学生信息      
  &ensp;&ensp;  属性：number（学号），name（姓名），grade（年级）   
  2）把学生信息写入文件中
  &ensp;&ensp; 通过BufferedWriter方法将学生信息写入文件中  
  ### 3.建立文本文件A和文本文件B    
   * 创建空的文本文件A  
    存放古诗处理结果和学生信息（代表该学生所交作业）  
   * 文本文件B  
   存放未处理的古诗内容，如下所示：     
 ```
 汉皇重色思倾国御宇多年求不得杨家有女初长成养在深闺人未识天生丽质难自弃一朝选在君  
 王侧回眸一笑百媚生六宫粉黛无颜色春寒赐浴华清池温泉水滑洗凝脂侍儿扶起娇无力始是新  
 承恩泽时云鬓花颜金步摇芙蓉帐暖度春宵春宵苦短日高起从此君王不早朝承欢侍宴无闲暇春  
 从春游夜专夜后宫佳丽三千人三千宠爱在一身金屋妆成娇侍夜玉楼宴罢醉和春姊妹弟兄皆列  
 士可怜光采生门户遂令天下父母心不重生男重生女骊宫高处入青云仙乐风飘处处闻缓歌慢舞  
 凝丝竹尽日君王看不足渔阳鼙鼓动地来惊破霓裳羽衣曲九重城阙烟尘生千乘万骑西南行翠华  
 摇摇行复止西出都门百余里六军不发无奈何宛转蛾眉马前死花钿委地无人收翠翘金雀玉搔头  
 君王掩面救不得回看血泪相和流黄埃散漫风萧索云栈萦纡登剑阁峨嵋山下少人行旌旗无光日  
 <未完，待续>  
 
 ```
  ### 4. 处理文件   
   *  对文本文件B的处理    
    1）每7个汉字加入一个标点符号，奇数时加“，”，偶数时加“。”   
    2）属性  
        数组：长度为7（用于识别每七个汉字）  
        len：用于识别数组识别的汉字的下标值    
        Index：使其等于1，使用BufferedReader读取文件，让其读取从第一个汉字开始读取    
    3）加入一个标点符号，奇数时加“，”，偶数时加“。”  的方法    
       判断len是否等于-1(=-1的时候代表文件已经读取完毕）  
       不等于-1时执行if语句，从第一个汉字写入，如果index除以2余数为0就加句号和换行，否则加逗号   
    4）对每7个汉字进行 3） 的处理  
       将以上if方法放入while语句，每执行完一次if方法，index自加1，len更新为当前已读汉字的长度  
    5)处理完以上操作关闭写入和读取，并关闭文本文件A，B  
   *  处理好的结果保存到文本文件A中
    处理示意如下：    
  ```
  汉皇重色思倾国，御宇多年求不得。
  杨家有女初长成，养在深闺人未识。
  天生丽质难自弃，一朝选在君王侧。
  回眸一笑百媚生，六宫粉黛无颜色。
  春寒赐浴华清池，温泉水滑洗凝脂。
  侍儿扶起娇无力，始是新承恩泽时。
  云鬓花颜金步摇，芙蓉帐暖度春宵。
  春宵苦短日高起，从此君王不早朝。
  …………

  ```
  ### 5.统计古诗中某个字或词出现的次数     
   * 属性：  
     s:读取行数
     count：字数，初始值为0  
     str:用户输入的词  
     ch:数组（查找用户所找字）
   * 方法：    
     1）使用Scanner，让用户输入想要查找的关键词     
     2）使用While语句确保读取行数不为空     
     3）判断用户所找关键词是否在这首诗里面 （子字符串是否被包含在此字符串之中）     
        使用contains，布尔类型包含输入true,否则输出false     
     4）输入true，使用for语句使其检索这首诗的全部内容  
     5）在for语句里面嵌套判断用户所找关键词与文中相同的词   
        使用equals，判断内容相等    
   ### 6.异常处理  
   * 方法：    
     FileNotFoundException ：捕获文件是否存在  
     IOException：捕获文件路径是否正确 
 ## 核心方法
（1）通过文件字节输入流（对文件数据以字节的形式进行读取操作如读取图片视频等）打开文本文件A，B
  ```
  FileInputStream input=new FileInputStream("D:\\nei\\B.txt");
  FileOutputStream output=new FileOutputStream("D:\\nei\\A.txt");
  ```
（2）创建字符缓冲输出流和输入流    
  ```
  BufferedWriter writer = new BufferedWriter(new OutputStreamWriter(output));
  BufferedReader reader = new BufferedReader(new InputStreamReader(input));
  ```
（3）通过Scanner实例化学生      
```
System.out.println("请输入学生姓名，学号，班级：");
			   Scanner stu1=new Scanner(System.in);
			   String name=stu1.next();
			   String number=stu1.next();
			   String grade=stu1.next();
```
（4）将学生信息写入文件     
```
writer.write("学生基本信息："+name+"  "+ number +"   "+grade+"\n");
 ```
（5）每7个汉字加入一个标点符号，奇数时加“，”，偶数时加“。”               
```
char[] buff = new char[7];
	           int len = reader.read(buff);
	           int index = 1;
	           while (len != -1)
	             {
	                 writer.write(buff,0,len-2);
	                 if (index %2 ==0){
	                     writer.write("。\n");
	                 }else{
	                     writer.write("，");
	                 }
	                 len = reader.read(buff);
	                 index ++;
	             }
```
 (6)关闭文件和字符缓冲输入流             
```
        reader.close();
	      writer.close();
	      input.close();
			  output.close(); 
```
 (7)统计古诗中某个字或词出现的次数                
```
 FileInputStream input1=new FileInputStream("D:\\nei\\A.txt");
 BufferedReader reader1=new BufferedReader(new InputStreamReader(input1));
	   String s = reader1.readLine(); //读取行数
	   System.out.println("请输入想找字（可查找本字字数）：");
	   Scanner sc=new Scanner(System.in);//从键盘接收数据
	   String str=sc.nextLine();
	   char[] ch=str.toCharArray();
	   int count=0;
 while (s != null) //确定行数不为空
				{            
  boolean b=s.contains(str);//子字符串是否被包含在此字符串之中,包含输出true，否则输出false
			String[] st=new String[s.length()-ch.length+1];			
			if(b==true)
			{
				for(int i=0;i<st.length;i++)
				{
					st[i]= s.substring(i,i+ch.length);
					if(st[i].equals(str))
					{
						count++;
					}
				}
			}
			s = reader1.readLine(); 
	} 
		System.out.println("包含  "+str+"   次数为："+count);//调用count，输出包含次数
}
```
(8)异常                
```
	 try {
	 }catch(FileNotFoundException e)
		  {
		   System.out.println("找不到文件");
		  }
		  catch(IOException e)
		  {
		   System.out.println("输入路径有误，请输入正确的路径");
		  }
```
## 实验结果
### （1）文本文件B        
![alt console](http://m.qpic.cn/psc?/V528qTS74BHGMM1h1AFf33VeSW0R67RO/ruAMsa53pVQWN7FLK88i5r3nwUBkZR9MGuAwjyIt9vvLsj3z6XaYoAgdw1Q4DiBXzgGSoqEDFRKjkJmfNZp4bcPQP5ShrdAInkniCP*EPH0!/b&bo=kwUyAZMFMgEDCSw!&rf=viewer_4)   
### （2）文本文件A     
![alt console](http://m.qpic.cn/psc?/V528qTS74BHGMM1h1AFf33VeSW0R67RO/45NBuzDIW489QBoVep5mcV3JOVtduWzNN5PF5Nf0*RioVV0nO7QqCFGwPjKViTVom1diXFSy8dRPPqrB2Nvuy6XqZFfYwiiGsXm01VT140g!/b&bo=GgLbAhoC2wIDGTw!&rf=viewer_4)       
### （3）统计关键词次数       
![alt console](http://m.qpic.cn/psc?/V528qTS74BHGMM1h1AFf33VeSW0R67RO/ruAMsa53pVQWN7FLK88i5r0vI00lZXOJwngWDuq0ji.Wy27VfQ3qDTMrJIF5.FRaUfVEqeB1Sg9rozXZxMqYIDiY6G4hpeRP*Gc8hsY.3mA!/b&bo=MQLgADEC4AADCSw!&rf=viewer_4)   
## 实验感想
  此次试验模拟学生作业处理，掌握了字符串的使用方法，以及通过String对文件的输入与输出，并学会了如何统计一篇文章某个字的次数，并且掌握了异常的处理结构以及使用。通过此次实验对String有了更深一步的认识，更好的学习编程。
