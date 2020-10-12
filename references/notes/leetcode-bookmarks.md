# Discussions/Posts
1. [10-line template that can solve most 'substring' problems](https://leetcode.com/problems/minimum-window-substring/discuss/26808/here-is-a-10-line-template-that-can-solve-most-substring-problems)

2. [Loop ordering in number of ways to make a target](https://leetcode.com/problems/coin-change-2/discuss/141076/Logical-Thinking-with-Clear-Java-Code/260611)

    - coins:`c[1], …, c[n]`, target:`t`

    - Duplicates allowed
      
        - ordering matters (`#sequences`)
          
            - ```
              dp[t+1] = {0}
                dp[0] = 1
                for s in 1, ..., t:
                    for i in 1, ..., n:
                        if(c[i] <= s) dp[s] += dp[s-c[i]]
                ```
            
        - ordering doesn't matter (`#sets`) 
        
            - ```
                dp[t+1] = {0}
                dp[0] = 1
                for i in 1, ..., n:
                    for s in 1, ..., t:
                        if(c[i] <= s) dp[s] += dp[s-c[i]]
                ```
        
    - Duplicates not allowed (`#sequences = #sets`)
        
        - ```
            dp[2, t+1] = {0}
            dp[0, 0] = 1
            for i in 1, ..., n:
                for s in 1, ..., t:
                    dp[i&1, s] = d[!(i&1), s]
                    if(c[i] <= s) dp[i&1, s] += d[!(i&1), s-c[i]]
            ```

