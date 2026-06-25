# Fundamentos do Rust

Este README apresenta de forma concisa os conceitos fundamentais da linguagem Rust, útil para iniciantes que desejam entender a filosofia e as construções básicas.

## Índice
- Introdução
- Instalação
- Conceitos essenciais
	- Variáveis e mutabilidade
	- Tipos e inferência
	- Controle de fluxo
	- Funções
	- Ownership (propriedade)
	- Borrowing & References
	- Lifetimes
	- Structs e Enums
	- Pattern Matching
	- Modules, Crates e Cargo
	- Tratamento de erros
	- Genéricos e Traits
	- Testes

## Introdução
Rust é uma linguagem de sistemas focada em segurança de memória, concorrência e performance. Fornece garantias em tempo de compilação que evitam erros comuns como data races e use-after-free.

## Instalação
Instale o toolchain oficial com rustup:

```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

Use `cargo` (ferramenta padrão) para criar, compilar e testar projetos:

```
cargo new nome_projeto
cargo build
cargo run
cargo test
```

## Conceitos essenciais

- Variáveis e mutabilidade
	- Por padrão variáveis são imutáveis: `let x = 5;`
	- Para mutabilidade: `let mut x = 5;`

- Tipos e inferência
	- Rust é estaticamente tipada, mas possui inferência: `let s = "texto";`
	- Tipos primitivos: inteiros, float, bool, char, tuplas, arrays

- Controle de fluxo
	- `if`, `else`, `loop`, `while`, `for` (iteração sobre iteradores)

- Funções
	- Declaradas com `fn nome(args) -> Tipo { ... }`
	- Expressões retornam valor sem `return` quando último item é expressão

- Ownership (propriedade)
	- Cada valor tem um único dono (binding). Ao mover (move), o dono anterior não pode usar o valor.
	- Evita cópias implícitas e controla tempo de vida da memória sem GC.

- Borrowing & References
	- Pode-se emprestar com referências imutáveis `&T` (muitos empréstimos simultâneos) ou referência mutável `&mut T` (apenas uma por vez).
	- Regras do borrow checker garantem segurança em tempo de compilação.

- Lifetimes
	- Anotações que descrevem o tempo de vida das referências quando não são óbvias ao compilador.

- Structs e Enums
	- `struct` define tipos compostos nomeados. `enum` define variantes somadas (ex.: `Option`, `Result`).

- Pattern Matching
	- `match` e `if let`/`while let` para decompor valores e controlar fluxo de forma segura.

- Modules, Crates e Cargo
	- Organização: módulos (`mod`), crates (pacotes), workspaces.
	- Cargo gerencia dependências e build.

- Tratamento de erros
	- Erros recuperáveis: `Result<T, E>`; use `?` para propagar erros.
	- Erros não recuperáveis: `panic!()`.

- Genéricos e Traits
	- Genéricos permitem escrever código que funciona com múltiplos tipos.
	- Traits definem comportamento compartilhado (interfaces/contratos).

- Testes
	- Escreva testes com `#[cfg(test)]` e `#[test]`. Execute com `cargo test`.

## Boas práticas rápidas
- Prefira tipos e APIs que deixam invariantes explicitamente.
- Use `clippy` para linting: `cargo clippy`.
- Documente com comentários `///` e gere docs com `cargo doc`.

## Recursos adicionais
- Livro oficial: https://doc.rust-lang.org/book/
- Rust by Example: https://doc.rust-lang.org/rust-by-example/
- Ferramentas: rustfmt, clippy, cargo

Bom estudo!
