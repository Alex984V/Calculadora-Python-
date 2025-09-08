# Documentação da Calculadora em Python

## 1. Funções

### Função `linha()`

Imprime uma linha de separação para melhorar a visualização no terminal.

```python
def linha():
    lin = "_"*120
    print(lin)
```

* Cria uma linha com 120 underscores (`_`).
* Utilizada para separar seções na tela.

---

### Função `mostrar_resultado(valor)`

Exibe o valor atual da operação.

```python
def mostrar_resultado(valor):
    linha()
    print("Valor no momento:", valor)
    linha()
```

* Mostra o valor acumulado no momento.
* Chama a função `linha()` antes e depois para organização visual.

---

### Função `não0(re, Numero)`

Evita divisão por zero, solicitando que o usuário escolha outra operação.

```python
def não0(re, Numero):
    while True:
        OP2 = input("Digite uma operação diferente de divisão por zero [MU, SO, SU,]: ").lower()

        if OP2 == "mu":
            return re * Numero
        elif OP2 == "so":
            return re + Numero
        elif OP2 == "su":
            return re - Numero
        else:
            print("Operação inválida! Tente novamente.")
```

* Recebe o valor atual (`re`) e o número que causaria divisão por zero.
* Permite escolher outra operação válida: multiplicação (`MU`), soma (`SO`) ou subtração (`SU`).
* Repete até que o usuário escolha corretamente.

---

### Função `conta(*num)`

Realiza operações matemáticas com uma lista de números e operações escolhidas pelo usuário.

```python
def conta(*num):
    OP = "text"
    re=0
    contar = len(num) - 1
    contador = 0
    resto = 0
    for Numero in num:
        contador += 1
        if contador != 1:
            # Mostra informação sobre o próximo número
        if re == 0 and contador ==1:
            re = Numero
        else:
            while True:
                mostrar_resultado(re)
                OP = input("Digite a operação desejada: ")
                # Verifica a operação e realiza cálculo
                # MU, DI, DR, SO, SU
                # Trata divisão por zero usando não0() se necessário
```

**Detalhes importantes:**

* Aceita qualquer quantidade de números (`*num`).
* Para cada número após o primeiro, solicita operação.
* Suporta operações:

  * `MU` -> Multiplicação
  * `DI` -> Divisão inteira (retorna quociente e resto)
  * `DR` -> Divisão real (float)
  * `SO` -> Soma
  * `SU` -> Subtração
* Divide por zero é tratado com `não0()`.
* Mantém variável `resto` para divisões inteiras que não dividem exatamente.

---

## 2. Fluxo do programa

1. Solicita ao usuário números separados por espaço:

```python
entrada = input("Digite os numeros separados por espaço: ")
valores = [int(x) for x in entrada.split()]
```

* Converte a entrada em lista de inteiros.

2. Mostra instruções para o usuário:

```python
print("Bem vindo a calculadora, agora digite a operação desejada")
print("Sendo [MU],[DI],[DR],[SO],[SU]")
linha()
```

3. Chama a função `conta()` para processar os números e operações:

```python
print("Resultado: ",conta(*valores))
linha()
```

* Exibe o resultado final.
* Mostra o resto da divisão, se houver.

---

## 3. Observações

* A calculadora é **interativa**, pedindo operações para cada número após o primeiro.
* Usa tratamento de erros para **divisão por zero**.
* As funções `linha()` e `mostrar_resultado()` melhoram a legibilidade do terminal.
* Permite operações mistas entre números (ex: soma com multiplicação e divisão).
* A função `conta` centraliza toda a lógica do cálculo, mantendo rastreio do valor atual (`re`) e do resto em divisões inteiras.

---

**Relação entre funções:**

* `conta()` chama `mostrar_resultado()` e `não0()` quando necessário.
* `não0()` é acionada apenas quando o usuário tenta dividir por zero.
* `linha()` é usada para separar visualmente seções de informações no terminal.
