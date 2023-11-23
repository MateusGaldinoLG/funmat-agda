
# Capítulo 1 - Naturais e Teoria dos Tipos

## Capítulo 1.1 - O tipo dos naturais

Para começar com essas notas, é necessário definir o que é um tipo. Para isso, vamos usar a definição que o livro Homotopy Type Theory (ou só HoTT-book) utiliza. Um tipo é como uma coleção de elementos, chamados de termos. Cada termo prova que o tipo é válido. Para denotar que "a é um elemento do tipo A", denotamos por "a : A". Na teoria dos Tipos, todo objeto possui um tipo (até mesmo tipos, mas vamos falar sobre isso depois).

Vamos definir o primeiro tipo em Agda, que será o tipo dos naturais

```agda

open import Cap0

data ℕ : Type where
  zero : ℕ
  suc : ℕ → ℕ
  
```
Explicações
* O Texto "open import Cap0" importa algumas definições sintáticas do "capítulo 0".
* A notação ℕ pode ser feita utilizando "\bN" no editor e → como "\to"
* "suc" é chamado de sucessor e é no pensamento popular  equivalente ao "+1", então suc zero pode ser entendido como "0+1 = 1" e assim por diante. Observe que a soma ainda não foi definida.

Para que Agda entenda a notação de suc zero = 1, suc (suc zero) = 2, etc. Vamos utilizar um *pragma*, que não tem relação direta com a teoria dos tipos e sim com a linguagem Agda.

```agda
{-# BUILTIN NATURAL ℕ #-}

```

Sejam dois elementos de um tipo  A, a : A e b : A, podemos definir o tipo "a =A b". Como todo tipo precisa de um elemento para ser verdadeiro, se encontrarmos um elemento de "a =A b", podemos dizer que a e b são *proposicionalmente iguais*. Mas podemos dizer também que a ≡ b : A, onde a e b são *iguais* por juizo ou *iguais por definição*.

Vamos definir o tipo das igualdades chamando-o de ≡

```agda
data _≡_  {A : Type} (x : A) : A → Type where
  instance refl : x ≡ x

{-# BUILTIN EQUALITY _≡_ #-}
```

Essa definição pode ser lida como: "Seja A um tipo e x um elemento do tipo A, definimos refl como a igualdade de x com x". Ou seja, para todo tipo A, a igualdade "x =A x" possui um elemento chamado de reflexividade (refl) que equivale à reflexividade da igualdade.


