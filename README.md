# fallout-terminal-cracker
def compare(s1,s2):
    x=0
    for i in range(len(s1)):
        if s1[i]==s2[i]:
            x+=1
    return(x)
def coeff(a,s):
    l=[0 for i in range(len(a)+1)]
    for i in s:
        l[compare(a,i)]+=1
    return(max(l))
def suggest_input(s):
    x=-1
    min_coeff=len(s)+1
    for i in s:
        c=coeff(i,s)
        if min_coeff>c:
            x,min_coeff=i,c
    return(x)
def delete_unneeded(inp,s,x):
    s_new=set()
    for i in s:
        if compare(inp,i)==x:
            s_new.add(i)
    return(s_new)
s=set()
a=input()
while a!=".":
    s.add(a)
    a=input()
for i in range(3):
    k=suggest_input(s)
    print(k)
    x=int(input())
    s=delete_unneeded(k,s,x)
    if len(s)==1:
        break
for i in s:
    print(i)
