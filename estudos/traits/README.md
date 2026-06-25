# Traits em Rust

Traits são um mecanismo de abstração em Rust que descreve comportamento comum que tipos diferentes podem compartilhar.

- Um trait define métodos que podem ser implementados por diferentes tipos.
- Um tipo implementa um trait para garantir que possui os métodos e funcionalidades especificados.
- Traits permitem escrever código genérico e reutilizável.

Exemplo simples:

```rust
trait Exibir {
    fn exibir(&self);
}

struct Pessoa {
    nome: String,
}

impl Exibir for Pessoa {
    fn exibir(&self) {
        println!("Nome: {}", self.nome);
    }
}
```

Aqui, o trait `Exibir` define um método `exibir`, e a struct `Pessoa` implementa esse trait.

Traits são parecidos com interfaces em outras linguagens, mas em Rust também suportam métodos com implementação padrão e podem ser usados para limites de tipos genéricos.
