# Ownership em Rust

## O que é Ownership?

Ownership (propriedade) é um sistema de gerenciamento de memória do Rust que permite que o compilador gerencie automaticamente a alocação e desalocação de memória sem necessidade de um garbage collector. É um dos conceitos mais importantes do Rust.

## As Três Regras de Ownership

1. **Cada valor tem um proprietário (owner)**
   - Todo valor em Rust tem uma variável que é seu proprietário responsável

2. **Um valor pode ter apenas um proprietário por vez**
   - A propriedade é exclusiva, não pode haver múltiplos proprietários simultaneamente

3. **Quando o proprietário sai do escopo, o valor é automaticamente liberado**
   - A memória é liberada automaticamente quando a variável deixa o escopo

## Exemplo Básico

```rust
fn main() {
    // s1 é o proprietário da String
    let s1 = String::from("hello");
    
    // A propriedade é transferida para s2
    // s1 não é mais válido após esta linha
    let s2 = s1;
    
    // Isto causaria um erro:
    // println!("{}", s1);  // erro: s1 não possui mais o valor
    
    println!("{}", s2);  // OK: s2 agora é o proprietário
}
```

## Move vs Copy

### Move (Transferência de Propriedade)
Para tipos complexos como `String`, a atribuição move a propriedade:

```rust
let s1 = String::from("rust");
let s2 = s1;  // Move: propriedade transferida
// s1 não é mais válido
```

### Copy (Cópia)
Para tipos simples como números, a atribuição faz uma cópia:

```rust
let x = 5;
let y = x;  // Copy: valor copiado
println!("{}, {}", x, y);  // Ambos são válidos
```

## Borrowing (Empréstimo)

Para usar um valor sem transferir a propriedade, usamos referências (`&`):

```rust
fn main() {
    let s1 = String::from("rust");
    
    // Empréstimo imutável: apenas leitura
    let len = calculate_length(&s1);
    
    println!("Length of '{}' is {}", s1, len);  // s1 ainda é válido
}

fn calculate_length(s: &String) -> usize {
    s.len()
}  // s sai do escopo, mas não possui o valor, portanto nada acontece
```

## Referências Mutáveis

Para modificar um valor emprestado, usamos referência mutável (`&mut`):

```rust
fn main() {
    let mut s = String::from("hello");
    
    change(&mut s);  // Empréstimo mutável
    
    println!("{}", s);  // Imprime: hello world
}

fn change(s: &mut String) {
    s.push_str(" world");
}
```

### Restrição: Uma Única Referência Mutável

Você não pode ter múltiplas referências mutáveis ao mesmo valor simultaneamente:

```rust
let mut s = String::from("rust");

let r1 = &mut s;
// let r2 = &mut s;  // ERRO: não pode ter duas referências mutáveis
```

## Regras de Borrowing

1. Em qualquer ponto, você pode ter **uma** referência mutável OU **múltiplas** referências imutáveis
2. Referências devem sempre ser válidas
3. Não pode haver mistura de referências mutáveis e imutáveis no mesmo escopo

## Benefícios do Ownership

✅ **Memory Safety**: Previne buffer overflows e use-after-free  
✅ **Sem Garbage Collector**: Melhor performance  
✅ **Sem Deadlocks**: Sistema de tipos impede certos erros de concorrência  
✅ **Eficiência**: Zero-cost abstractions
