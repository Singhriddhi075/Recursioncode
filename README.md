# Recursioncode
recursion code in java .
//getpermutation
public class getpermutation {

	public static void main(String[] args) {
		System.out.println(getpermutation("abc"));

	}
	public static ArrayList<String> getpermutation(String str){
		if(str.length()==0) {
			ArrayList<String> br=new ArrayList<>();
			br.add("");
			return br;
		}
		char ch=str.charAt(0);
		String ros=str.substring(1);
		ArrayList<String> rr=getpermutation(ros);
		ArrayList<String> mr=new ArrayList<>();
		for(String rrs:rr) {
			for(int i=0;i<=rrs.length();i++) {
				String val=rrs.substring(0,i)+ch+rrs.substring(i);
				mr.add(val);
			}
		}
		return mr;
		
	}

}
//lexicographicprint.java
public class lexicographicprint {

	public static void main(String[] args) {
//	lexicocounting(2,1000);
		Scanner scn = new Scanner(System.in);
        int n=scn.nextInt();
		String s = scn.next();
		int[][] strg = new int[s.length()][s.length()];
		for (int i = 0; i < strg.length; i++) {
			Arrays.fill(strg[i], -1);
		}

		palidromepartition(s, "");

	}

	public static void lexicocounting(int curr, int n) {
		if (curr > n) {
			return;
		}
		System.out.println(curr);
		int i = 0;
		if (curr == 0) {
			i = 1;
		}
		while (i <= 9) {

			lexicocounting(curr * 10 + i, n);
			i++;
		}
	}

	public static void palidromepartition(String ques, String ans) {
		if (ques.length() == 0) {
			System.out.println(ans);
			return;
		}
		for (int i = 1; i <= ques.length(); i++) {
			String part = ques.substring(0, i);
			String roq = ques.substring(i);

//			System.out.println(part + " " + roq);
			if (ispalidrome(part))
				
			palidromepartition(roq, ans + part + " ");
		}
	}

	public static boolean ispalidrome(String str) {
		int left = 0;
		int right = str.length() - 1;
		while (left <= right) {
			if (str.charAt(left) != str.charAt(right)) {
				return false;
			}
			left++;
			right--;
		}
		return true;
	}

}
//recursion.java
public class recursion {

	public static void main(String[] args) {
		
//     PD(5);
//		PI(5);
//		PDI(5);
//		PDIskip(5);
//		System.out.println(Fact(4));
//		System.out.println(power(2,3));
		int[] arr= {6,8,1,1,2,8,4};
//		System.out.println(firstindex(arr,0,8));
//		System.out.println(lastindex(arr,0,8));
//     int[] ans=allindicies(arr,0,8,0);
//     display(ans);   write array display code
		System.out.println(getSS("abc"));
	}
//	when stack is building
	public static void PD(int n) {

//		base case-at which point code should stop
		if(n==0) {
			return;
		}
		System.out.println(n);
		PD(n-1);
	}
//	when stack is removing
	public static void PI(int n) {
		if(n==0) {
			return;
		}
		PI(n-1);
		System.out.println(n);
	}
	public static void PDI(int n) {
		if(n==0) {
			return;
		}
		System.out.println(n);
		PDI(n-1);
		System.out.println(n);
	}
	public static void PDIskip(int n) {
		if(n==0) {
			return;
		}
		if(n%2==1) {
			System.out.println(n);
		}
		PDIskip(n-1);
		if(n%2==0) {
			System.out.println(n);
		}
	}
 
    public static int Fact(int n) {
    	 if(n==1) {
    		 return 1;
    	 }
    	int fnm1=Fact(n-1);
    	int fn=n*fnm1;
    	return fn;
     }
    public static int power(int X,int n) {
    	if(n==0) {
    		return 1;
    	}
    	int POnm1=power(X,n-1);
    	int PO=X*power(X,n-1);
    	return PO;
    }
    public static int firstindex(int[] arr,int si,int data) {
    	if(si==arr.length) {
    		return -1;
    	}
    	if(arr[si]==data) {
    		return si;
    	}else {
    		int restAns=firstindex(arr,si+1,data);
    		return restAns;
    	}
    }
    public static int lastindex(int[] arr,int si,int data) {

	 if(si==arr.length) {
		 return -1;
	 }
	 int index=lastindex(arr,si+1,data);
	 if(index==-1) {
		 if(arr[si]==data) {
			 return si;
		 }else {
			 return-1;
		 }
	 }else {
		 return index;
	 }
	 
 }
    
    
    public static int[]  allindicies(int[] arr,int si,int data,int count) {

    	if(si==arr.length) {
    		int[] base=new int[count];
    		return base;
    	}
    	int[] indices=null;
    	if(arr[si]==data) {
    		indices=allindicies(arr,si+1,data,count+1);
    		
    	}else {
    		indices=allindicies(arr,si+1,data,count);
    	}
    	if(arr[si]==data) {
    		indices[count]=si;
    	}
    	return indices;
    }
    public static ArrayList<String> getSS(String str){
    	if(str.length()==0) {
    		ArrayList<String> baseresult=new ArrayList<>();
    		baseresult.add("");
    		return baseresult;
    	}
    	char cc=str.charAt(0);
    	String ros=str.substring(1);
    	ArrayList<String> myresult=new ArrayList();
    	ArrayList<String> resResult=getSS(ros);
    	for(int i=0;i<resResult.size();i++) {
    		myresult.add(resResult.get(i));
    		resResult.add(cc+resResult.get(i));
    	}
    	return myresult;
    }
    
    
}
//Recursionprint.java
public class Recursionprint {

	public static void main(String[] args) {
		validparanthesis(3,0,0,"");

	}
	public static void validparanthesis(int n,int open,int close,String ans) {
//		positive base case
		if(open==close&&open==n) {
			System.out.println(ans);
			return;
		}
//		negative base case
		if(open>n||close>open) {
			return;
		}
		validparanthesis(n,open+1,close,ans+"(");
		validparanthesis(n,open,close+1,ans+")");
	}

}
//recursion sorting
public class Recursionsorting {
	static Scanner scn=new Scanner(System.in);
	public static void main(String[] args) {
		
		int[] arr=takeinput();
         int[] ans=mergesort(arr,0,arr.length-1);
         for(int val:ans) {
        	 System.out.println(val+" ");
         }
         System.out.println(arr);
 
	}
	public static int[] takeinput() {
		int n=scn.nextInt();
        int[] arr=new int[n];
        for(int i=0;i<arr.length;i++) {
        	arr[i]=scn.nextInt();
        }
        return arr;
	}
	public static int[] mergetwoSortedArray(int[] arr1,int[] arr2) {
		
		
		int[] merged=new int[arr1.length+arr2.length];
		int i=0;
		int j=0;
		int k=0;
		while(i<arr1.length && j<arr2.length) {
			if(arr1[i]<=arr2[j]) {
				merged[k]=arr1[i];
				i++;
			}else {
				merged[k]=arr2[j];
				j++;
				k++;
			}
		}
		
		if(i==arr1.length) {
			while(j<arr2.length) {
				merged[k]=arr2[j];
				j++;
				k++;
			}
		}
		if(j==arr2.length) {
			while(i<arr1.length) {
				merged[k]=arr1[i];
				i++;
				k++;
			}
		}
		
		return merged;
	}
     
	public static int[] mergesort(int[] arr,int lo,int hi){
		 
		
		if(lo==hi) {
			int[] br=new int[1];
			br[0]=arr[lo];
			return br;
		}
    	 int mid=(lo+hi)/2;
    	int[] fh= mergesort(arr,lo,mid);
    	int[] sh= mergesort(arr,mid+1,hi);
    	   
    	int[] merge=mergetwoSortedArray(fh,sh);
    	return merge;
     }
}
//recursion subsequence
public class recursionsubsequence {

	public static void main(String[] args) {
		Scanner scn=new Scanner(System.in);
		int n=scn.nextInt();
		String[] arr=new String[n];
		for(int i=0;i<n;i++) {
			arr[i]=scn.next();
			
		}
		for(int i=0;i<n;i++) {
			display(Lexo(GetSS(arr[i])));
		}
	}
		static ArrayList<String> GetSS(String str){
			if(str.length()==0) {
				ArrayList<String>  BR=new ArrayList<>();
				BR.add("");
				return BR;
			}
			char cc=str.charAt(0);
			String ros=str.substring(1);
			ArrayList<String> MR=new ArrayList<>();
			ArrayList<String> RR=GetSS(ros);
			for(int i=0;i<str.length();i++) {
				MR.add(RR.get(i));
				MR.add(cc+RR.get(i));
				
			}
			return MR;
		}
		public static ArrayList<String> Lexo(ArrayList<String> str){
			for(int i=0;i<str.size()-1;i++) {
				for(int j=i+1;j<str.size();j++) {
					if(str.get(i).compareTo(str.get(j))>0) {
						String tmp=str.get(i);
						str.set(i, str.get(j));
						str.set(j, tmp);
					}
				}
		}
			return str;

	}
		public static void display(ArrayList<String> str) {
			for(int i=0;i<str.size();i++) {
				System.out.println(str.get(i));
			}
		}

}


