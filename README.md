# Minimum-Edit-Distance-Implementation-for-String (Character Based Distance)
Implementation of Minimum Edit Distance Algorithm from scratch in Python. Minimum Edit Distance Calculates the distance between two strings Character Based Distance
<h3>Levenshtein Distance</h3>
– No. of edits between two words/strings
– Costs
• Insertion = Deletion = 1
• Substitution = insertion + deletion = 2 (except substitution of
identical characters, which costs 0)
– E.g. from

        I N T E N * T I O N
        * E X E C U T I O N
        D S S S I = 8
        
Set the cost in .ipynb file in following cell:
    del_cost=1
    ins_cost=1
    sub_cost=2
    
Then pass the strings in Function Parameter. It will output the minimun edit distance between the strings. There are two params in function source string and destination string

      #Character Based Distance
      def Calculate_Minimum_edit_distance(source,target):    
          n= len(source)
          m= len(target)
          MED_Matrix= np.zeros((n+1,m+1), dtype='int32')
          for i in range(1,n+1):
              MED_Matrix[i][0]=MED_Matrix[i-1][0]+del_cost
          for i in range(1,m+1):
              MED_Matrix[0][i]=MED_Matrix[0][i-1]+del_cost   
          for i in range(1,n+1):
              for j in range(1,m+1):
                  if(source[i-1]==target[j-1]):
                      MED_Matrix[i][j]=min([MED_Matrix[i-1][j]+del_cost,MED_Matrix[i-1][j-1]+0,MED_Matrix[i][j-1]+ins_cost])
                  else:
                      MED_Matrix[i][j]=min([MED_Matrix[i-1][j]+del_cost,MED_Matrix[i-1][j-1]+sub_cost,MED_Matrix[i][j-1]+ins_cost])
          #print(np.matrix(MED_Matrix))
          #print(MED_Matrix[n][m])
          return MED_Matrix[n][m]
