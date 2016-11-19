# Helloworld
New Repository
Hello fellow beings..
here is a java program i've been working on, its to convert number to words. i have managed to convert upto 9,223,372,036,854,775,806 
(Nine Quintillion Two Hundred Twenty Three Quadrillion Three Hundred Seventy Two Trillion Thirty Six Billion Eight Hundred Fifty Four Million Seven Hundred Seventy Five Thousand Eight Hundred Six). the limit that a "long" data-type can hold. 
Is there any other way to implement much higher numbers like say a googolplex.
 Here's the code..
 

package numericconvert;

import java.util.Scanner;

/**
 *
 * @author Vineeth
 */
public class NumericConvert {

    public static void main(String[] args) {
        long num=0;
        String numtoWord ="";
        System.out.println("Enter a number :");
        Scanner sin = new Scanner(System.in);
        num= sin.nextLong();
        numtoWord = numCon(num);
        System.out.println(num+ "  "+numtoWord);
    }
        private static final String numNames[]= {" ","One","Two","Three","Four","Five","Six","Seven","Eight","Nine","Ten","Eleven","Twelve","Thirteen","Fourteen","Fifteen","Sixteen","Seventeen","Eighteen","Nineteen",};
        private static final String tenNames[]= {" ","Twenty","Thirty","Fourty","Fifty","Sixty","Seventy","Eighty","Ninety"};
        private static final String bigNums[] = {" ","Hundred","Thousand","Million","Billion","Trillion","Quadrillion","Quintillion","Sextillion","Septillion","Octillion","Nonillion","Decillion",""};
    static String numCon(long n){
        long num=0,rem=0; 
        int count=0;
        String s=null, s1=null;
        num=n;
        while(num!=0){
        rem=num%10;
        num=num/10;
        count++;
        }
        if(n<0){
            return "Negative " +numCon(-n);
        }while(n>0){
            long i=0;
            System.out.println(" "+count);
        switch(count){
            case 1: return ones_tens(n);
            case 2: return ones_tens(n);  
            case 3: return hundreds(n);
            case 4 : case 5: return thousands(n);
            case 6: {
                        s=numCon(n/1000) +" "+bigNums[2];
                        if(n%1000==0||n%10000==0||n%100000==0){
                        return s;
                        }
                        else {
                            s1=numCon(n%1000);
                            return s+" "+s1;
                        }
                    }
            case 7: case 8: case 9: {
                        i = (long) Math.pow(10, 6);
                        s = numCon(n/i)+" "+bigNums[3];
                        if(n%i==0 || n%((long) Math.pow(10, 7))==0 || n%((long) Math.pow(10, 8))==0){
                        return s;
                        }else
                        {
                            s1=numCon(n%i);
                            return s+" "+s1;
                        }
                        }
            case 10: case 11: case 12: {
                    i = (long) Math.pow(10, 9);
                    s = numCon(n/i)+" "+bigNums[4];
                    if(n%i==0 || n%((long) Math.pow(10, 10))==0 || n%((long) Math.pow(10, 11))==0){
                    return s;
                    }else
                    {
                        s1=numCon(n%i);
                        return s+" "+s1;
                    }
                    } 
            case 13: case 14: case 15: {
                    i = (long) Math.pow(10, 12);
                    s = numCon(n/i)+" "+bigNums[5];
                    if(n%i==0 || n%((long) Math.pow(10, 13))==0 || n%((long) Math.pow(10, 14))==0){
                    return s;
                    }else
                    {
                        s1=numCon(n%i);
                        return s+" "+s1;
                    }
                    }
            case 16: case 17: case 18: {
                    i = (long) Math.pow(10, 15);
                    s = numCon(n/i)+" "+bigNums[6];
                    if(n%i==0 || n%((long) Math.pow(10, 16))==0 || n%((long) Math.pow(10, 17))==0){
                    return s;
                    }else
                    {
                        s1=numCon(n%i);
                        return s+" "+s1;
                    }
                    }
            case 19: case 20: case 21: {
                    i = (long) Math.pow(10, 18);
                    s = numCon(n/i)+" "+bigNums[7];
                    if(n%i==0 || n%((long) Math.pow(10, 19))==0 || n%((long) Math.pow(10, 20))==0){
                    return s;
                    }else
                    {
                        s1=numCon(n%i);
                        return s+" "+s1;
                    }
                    }
                    }                           
        }
        return null;
    } 

    
    static  String thousands(long num){
        int n = (int) num;
        String s=null, s1=null;
        if(n<=19999){
                    s= numNames[n/1000]+" "+bigNums[2];
                    s1=hundreds(n%1000);
                    if(n%1000==0 || n%10000==0){
                    return s;
                    } else return s+" "+s1;
                }
                else if (n>19999 && n<=99999) { 
                    s= tenNames[(n/10000)-1]+" "+ bigNums[2];
                    s1= hundreds(n%1000);
                    if(n%10000==0){
                      return s;
                    }
                    else{
                    n=n/1000;
                    s= tenNames[(n/10)-1]+" "+numNames[n%10]+" "+bigNums[2];
                    return s+" "+s1;
                    }
                }
        return null;
    }
    
    static String hundreds(long num){
        int n = (int) num;
        String s1= numNames[n/100] +" "+ bigNums[1];
        String s2= ones_tens(n%100);
        if(n<=99){
        return s2;
        }
        else if(n%100==0){
        return s1;
        }
        else return s1+" "+s2;
    }

    static String ones_tens(long num){
        int n = (int) num;
        if(n<20){
        return numNames[n];
        }
        String s = tenNames[(n/10)-1];
        if(n%10==0){
        return s;
        }
        return s+ " "+numNames[n%10];
    }  
}
   
