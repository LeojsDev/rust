# Estruturas em Rust

Em Rust, `structs` (estruturas) são tipos compostos que agrupam vários valores sob um único nome. Cada valor dentro de uma `struct` é chamado de campo, e cada campo pode ter um tipo diferente.

## Por que usar `structs`

- Organizar dados relacionados.
- Definir tipos personalizados mais claros.
- Passar múltiplos valores juntos de maneira segura.

## Exemplo básico

```rust
struct Pessoa {
    nome: String,
    idade: u32,
}

fn main() {
    let pessoa = Pessoa {
        nome: String::from("Alice"),
        idade: 30,
    };

    println!("Nome: {}, Idade: {}", pessoa.nome, pessoa.idade);
}
```

## Tipos de `struct`

- `struct` nomeada: usada com campos nomeados, como no exemplo acima.
- `tuple struct`: campos sem nome, acessados por posição.
- `unit-like struct`: sem campos, usada como marcador ou tipo zero-sized.

## Acesso e uso

Campos de `struct` são acessados com o operador `.`. Também é comum implementar métodos e funções associadas usando `impl`.

## Segurança

Rust garante segurança de memória e propriedade com `structs`, evitando referências inválidas e condições de corrida quando combinadas com o sistema de propriedade.
