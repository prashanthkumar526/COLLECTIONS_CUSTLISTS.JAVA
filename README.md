# COLLECTIONS_CUSTLISTS.JAVA
  
package www.prashanth.CustomList;
import java.io.*;
class MethodForCustomCollection
{
public Object[] objectArray=new Object[5];
public int elementCount=0;
public void add(Object obj)
{
  if(elementCount==objectArray.length)
 {
   increaseCapacity();
 }
objectArray[elementCount]=obj;
elementCount++;
}
public void increaseCapacity()
{
int newCapacity=(objectArray.length)*3;
Object[] newObjectArray=new Object[newCapacity];
 for(int i=0;i<objectArray.length;i++)
 {
   newObjectArray[i]=objectArray[i];
 } 
objectArray=newObjectArray;
}
public void remove(int index)
{
	if(index<0||index>=objectArray.length)
	{
		System.err.println("Index out of Bound Exception"+index);
	}
	while(index<objectArray.length-1)
	{
		objectArray[index]=objectArray[index+1];
		index++;
     }
	objectArray[index]=null;
	elementCount--;
}
public Object get(int retrivalIndex)
{
	return objectArray[retrivalIndex];
}
}

class CustomListAddOperation
{
public static void main(String[] args) throws IOException
{
InputStreamReader isr=new InputStreamReader(System.in);
BufferedReader br=new BufferedReader(isr);
MethodForCustomCollection objectForMethodOperation=new MethodForCustomCollection();
System.out.println("Enter size of List:");
String size=br.readLine();
int listsize=Integer.parseInt(size);
System.out.println("Enter Elements to add in List:");
for(int i=0;i<listsize;i++)
{
String objectadd=br.readLine();
objectForMethodOperation.add(objectadd);
}
System.out.println("Your Elements Of List After Adding:");
System.out.print("[");	
for(int i=0;i<objectForMethodOperation.objectArray.length;i++)
{
	System.out.print(objectForMethodOperation.objectArray[i]+",");
}
System.out.println("]");
System.out.println("enter index you want to remove:");
String removeindex=br.readLine();
int index=Integer.parseInt(removeindex);
objectForMethodOperation.remove(index);
System.out.println("Your Elements Of List After Removing:");
System.out.print("[");
for(int i=0;i<objectForMethodOperation.objectArray.length;i++)
{
	System.out.print(objectForMethodOperation.objectArray[i]+",");
}
System.out.println("]");
System.out.println("Enter The Retrival Index:");
String indexretrival=br.readLine();
int retrivalIndex=Integer.parseInt(indexretrival);
Object objretrival=objectForMethodOperation.get(retrivalIndex);
System.out.println("The Retrival Index Is:"+objretrival);
}
}
