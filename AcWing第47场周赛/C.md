import java.io.*;
import java.util.*;
import java.lang.*;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt(); int k = sc.nextInt();

        int[] nums = new int[k];
        for(int i = 0; i < k; i++) {
            nums[i] = sc.nextInt();
        }
        
        // 约瑟夫环问题，用队列来模拟
        int hh = 0, tt = -1;
        int[] queue = new int[10010];
        for(int i = 1; i <= n; i++) {
            queue[++tt] = i; 
        }
        
        for(int i = 0; i < k; i++) {
            int count = nums[i] % (tt - hh + 1);
            while(count-- > 0) {
                int temp = queue[hh++]; // 把队头元素取出来放到队尾去
                queue[++tt] = temp;
            }
            System.out.print(queue[hh++] + " ");
        }
    }
}
