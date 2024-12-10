## Sources :

- [Abstract Interpretation With Professor Patrick Cousot | Lecture Series on AI #11 | *J.P. Morgan*](https://www.youtube.com/watch?v=IBlfJerAcRw)
- [Abstract interpretation by *Ralf Laemmel*](https://www.youtube.com/watch?v=zCrnMvJgeUk)

## Interprétation abstraite

- Domaines abs
    - Interval
    - Parité
    - Chaîne de caractère (strcat(...))

$$a = [a_1,a_2]$$
$$b = [b_1,b_2]$$
$$a+1 = [a_1+1,a_2+1]$$
$$a+b = [a_1+b_1,a_2+b_2]$$
$$-b = [-b_2,-b_1]$$
$$a-b = [a_1-b_2, a_2-b_1]$$
$$p(a,b) = (a_1\times{b_1},a_1\times{b_2},a_2\times{b_1},a_2\times{b_2})$$
$$a*b = [min(p(a,b)), max(p(a,b))]$$

Exemple :
$$a=c+5+b$$
$$a=[c_1+5+b_1,c2+5+b_2]$$

Avec des nombres enrichis avec `input()` qui est entre $[-\infty;+\infty]$ ou $[-2^N;2^N]$. Si Nous sommes dans le domaine alors la réponse est vraie, sinon elle est fausse.

## Cas d'un simple `if/else`

```c
if(c<d){
    // Domaine de 'c' et de 'd' inclus
}
else {  // c >= d
    // Domaine de 'c' et de 'd' exclus
}
```
On place nos intervalles: $c = [-20,32]$ et $d = [4,64]$.

- `if`
    - $c = [-20,32]$ et $d = [4,64]$. On garde le même intervalle, car $-20 < 4$ et $32 < 64$
- `else`
    - $c = [4,32]$ et $d = [4,32]$
On change les intervalles pour faire en sorte que `c >= d`. On prend donc le maximum pour $c$ et le minimum pour $d$.

## Cas du `while`

```c
while(c<d)
{
    // inclus l'intervalle
}
// exclus
```

On élargie le domaine par l'intervalle le plus élevé

## Cas d'un `if/else` avec domaine changeant

```c
a=input();
b=a;
if(a>5)
    a = a+b;
else
    a=-a+5-b+5;
```
Soit les domaines suivants :
- $a=[-\infty;+\infty]$ et $b=[-\infty;+\infty]$
- **if:** $a=[6;+\infty]$ et $b=[-\infty;+\infty]$
- **else:** $a=[-\infty;+\infty]$ et $b=[6;+\infty]$

# Clause de Horn

m0 ==> m1

(m1 est implicite -> il faut avoir reçu m1 pour envoyer m2).

m0 & m2 ==> m3