```python
n1, n2, n3, n4 = map(float, input().split())

X = 0.2*n1 + 0.3*n2 + 0.4*n3 + 0.1*n4

print("Media: " + f'{X:.1f}')

if X >= 5 and X < 7:
    Y = float(input())
    print("Aluno em exame.")
    print("Nota do exame: " + f'{Y:.1f}')
    Z = (X + Y)/2
    if Z >= 5:
        print("Aluno aprovado.")
    else:
        print("Aluno reprovado.")
    print("Media final: " + f'{Z:.1f}')
elif X >= 7:
    print("Aluno aprovado.")
else:
    print("Aluno reprovado.")
```