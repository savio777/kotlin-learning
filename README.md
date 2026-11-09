# HelloWorld — estudos de Kotlin

[Android & Kotlin Development Masterclass – Full Course | 46:29](https://www.youtube.com/watch?v=blKkRoZPxLc)

Projeto só para aprender a linguagem Kotlin. O código fica em
`app/src/main/java/com/example/helloworld/Main.kt`, e a função `main()` é
executada direto na JVM, sem emulador nem celular.

## Pré-requisitos

- **Java (JDK 17 ou superior)**: confira com `java -version`
- **Compilador Kotlin (`kotlinc`)**: o Android Studio já vem com um. Para usá-lo
  no terminal, coloque-o no `PATH` (dá para pôr no `~/.zshrc` para ficar fixo):

  ```bash
  export PATH="$HOME/Downloads/Android/android-studio/plugins/Kotlin/kotlinc/bin:$PATH"
  ```

  Confira se funcionou:

  ```bash
  kotlinc -version
  ```

  > Outra opção é instalar o Kotlin à parte, com o [SDKMAN](https://sdkman.io/):
  > `sdk install kotlin`

## Rodando

Rode estes comandos a partir da raiz do projeto:

```bash
# 1. Compila o arquivo e gera um .jar executável (que já inclui o runtime do Kotlin)
kotlinc app/src/main/java/com/example/helloworld/Main.kt -include-runtime -d out/main.jar

# 2. Executa
java -jar out/main.jar
```

Saída esperada:

```
oi
```

### Em um comando só

```bash
kotlinc app/src/main/java/com/example/helloworld/Main.kt -include-runtime -d out/main.jar && java -jar out/main.jar
```

### Com vários arquivos `.kt`

Se você criar outros arquivos no mesmo pacote, compile a pasta inteira:

```bash
kotlinc app/src/main/java/com/example/helloworld/ -include-runtime -d out/main.jar && java -jar out/main.jar
```

> Se mais de um arquivo tiver uma função `main()`, escolha qual rodar pelo nome
> da classe gerada (o arquivo `Main.kt` vira `MainKt`):
>
> ```bash
> java -cp out/main.jar com.example.helloworld.MainKt
> ```

## REPL (testar código na hora)

Para experimentar trechos de Kotlin de forma interativa:

```bash
kotlinc -Xrepl
```

Digite o código (ex.: `println(1 + 2)`) e saia com `:quit`.

## Dicas

- A pasta `out/` só guarda os arquivos compilados e está no `.gitignore`.
- O primeiro `kotlinc` demora alguns segundos para iniciar. Isso é normal.
