# Guitar Healer

Projeto acadêmico desenvolvido em C++: um jogo musical simples inspirado em jogos de ritmo. LEDs coloridos descem por quatro pistas e o jogador pressiona a tecla correspondente quando cada nota chega à linha de referência.

## Como funciona

- A janela do jogo tem 360 × 600 pixels.
- As quatro pistas usam as cores vermelho, verde, amarelo e azul.
- O arquivo `Projeto_oficinas/Faixa.txt` define a velocidade das notas e a sequência de cada pista.
- A música usada pelo jogo está em `Projeto_oficinas/Super_Mario_Bros.ogg`.

### Controles

| Pista | Cor | Tecla |
| --- | --- | --- |
| 1 | Vermelho | `A` |
| 2 | Verde | `S` |
| 3 | Amarelo | `D` |
| 4 | Azul | `F` |

Mantenha a janela do jogo em foco para que as teclas sejam capturadas. A música começa aproximadamente 11,5 segundos após o início da execução.

## Requisitos

- Windows e Visual Studio 2022 com a carga de trabalho **Desenvolvimento para desktop com C++** (toolset v143).
- SFML 2.5.1, incluindo os módulos Graphics, Window, Audio, Network e System (o projeto também vincula Network).
- A biblioteca SFML compilada para a mesma arquitetura e configuração selecionadas no projeto (Win32/x86 ou x64; Debug ou Release).

## Compilar e executar

1. Instale ou extraia o SFML 2.5.1 em uma pasta local.
2. Abra `Projeto_oficinas.sln` no Visual Studio.
3. Nas propriedades do projeto **Projeto_oficinas**, atualize os caminhos de inclusão e biblioteca em **C/C++ → Geral → Diretórios de Inclusão Adicionais** e **Vinculador → Geral → Diretórios de Bibliotecas Adicionais** para apontarem à sua instalação do SFML. O arquivo do projeto contém caminhos absolutos de outra máquina, que precisam ser ajustados.
4. Selecione a configuração e arquitetura compatíveis com a sua instalação do SFML. Compile a solução e execute o projeto.
5. Configure o **Diretório de Trabalho** de depuração para `$(ProjectDir)` (pasta `Projeto_oficinas`). O programa procura `Faixa.txt` e `Super_Mario_Bros.ogg` usando caminhos relativos.
6. Garanta que as DLLs da SFML correspondentes à configuração estejam disponíveis junto ao executável ou no `PATH` do Windows.

## Formato da faixa

O arquivo `Projeto_oficinas/Faixa.txt` usa cinco linhas:

1. Um número inteiro que define o parâmetro de velocidade usado para mover as notas.
2. Uma sequência binária para a pista vermelha.
3. Uma sequência binária para a pista verde.
4. Uma sequência binária para a pista amarela.
5. Uma sequência binária para a pista azul.

Cada caractere da sequência representa uma posição: `1` ativa uma nota e `0` deixa a posição vazia. Não adicione espaços ou outros caracteres às sequências. O arquivo fornecido é a faixa de exemplo do projeto.

## Estrutura do projeto

```text
.
├── Projeto_oficinas.sln
└── Projeto_oficinas/
    ├── Projeto_oficinas.vcxproj
    ├── Projeto_oficinas.cpp   # ponto de entrada
    ├── jogo.*                 # inicialização do jogo
    ├── fase.*                 # execução, desenho e carregamento da faixa
    ├── gerEventos.*           # captura dos controles
    ├── fitaled.*              # pistas de LEDs
    ├── led.*                  # notas individuais
    ├── T_class.*              # estado compartilhado das threads
    ├── Faixa.txt              # sequência de exemplo
    └── Super_Mario_Bros.ogg   # música de exemplo
```

## Observações

O projeto é um protótipo acadêmico. A verificação de acerto desliga a nota correspondente; a implementação atual não exibe pontuação. A execução e a compilação dependem do Visual Studio e da SFML configurada localmente.


