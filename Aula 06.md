# Missão Prática: O Laboratorio de Arquitetura.

### 1. Versão Neutra:

**Gere um sistema que calcule a média de notas de um aluno. **

Resposta gerada - Aqui está um script simples em Python que recebe as notas, calcula a média e diz se o aluno foi aprovado (considerando a média 7.0).

```python
def calcular_media():
    print("--- Sistema de Notas ---")
    
    try:
        # Recebe a quantidade de notas
        qtd_notas = int(input("Quantas notas deseja inserir? "))
        notas = []

        # Coleta as notas
        for i in range(qtd_notas):
            nota = float(input(f"Digite a nota {i+1}: "))
            notas.append(nota)

        # Calcula a média
        media = sum(notas) / len(notas)

        # Exibe o resultado
        print(f"\nMédia final: {media:.2f}")

        if media >= 7:
            print("Status: APROVADO! 🎉")
        elif media >= 5:
            print("Status: RECUPERAÇÃO. 📝")
        else:
            print("Status: REPROVADO. ❌")
            
    except ValueError:
        print("Erro: Por favor, digite apenas números.")

# Executa o sistema
calcular_media()

```
Como funciona:
- Entrada dinâmica: Você escolhe quantas notas quer calcular (2, 3, 10, etc).
- Tratamento de erro: Se você digitar uma letra por engano, o programa não "quebra".
- Lógica de Aprovação: Já vem com critérios de corte (Aprovado, Recuperação ou Reprovado).

---

### 2. Versão Persona:

**Gere o sistema que calcule média de notas porém agora atue como um Desenvolvedor Sênior experiente e criterioso na área da programação e que precisa resolver esse problema.**

Resposta gerada - Para um cenário real, um script solto não escala. Como desenvolvedor sênior, foco em separação de responsabilidades, imutabilidade e extensibilidade.

Em vez de um input() genérico, estruturei o sistema seguindo princípios de Clean Code, tratando a lógica de negócio (cálculo) separada da interface (I/O).

Aqui está uma implementação robusta em Python:

```python
from dataclasses import dataclass
from typing import List, Optional
from enum import Enum

class Status(Enum):
    APROVADO = "Aprovado"
    RECUPERACAO = "Recuperação"
    REPROVADO = "Reprovado"

@dataclass(frozen=True)
class ConfigAvaliacao:
    """Configurações de negócio centralizadas."""
    MEDIA_CORTE: float = 7.0
    LIMITE_RECUPERACAO: float = 5.0

class CalculadoraAcademica:
    def __init__(self, config: ConfigAvaliacao = ConfigAvaliacao()):
        self._config = config

    def calcular_media(self, notas: List[float]) -> float:
        if not notas:
            return 0.0
        return sum(notas) / len(notas)

    def definir_status(self, media: float) -> Status:
        if media >= self._config.MEDIA_CORTE:
            return Status.APROVADO
        if media >= self._config.LIMITE_RECUPERACAO:
            return Status.RECUPERACAO
        return Status.REPROVADO

def executar_sistema():
    """Interface de usuário separada da lógica de cálculo."""
    app = CalculadoraAcademica()
    
    print("--- Sistema de Gestão de Notas (Enterprise Edition) ---")
    
    try:
        entrada = input("Digite as notas separadas por espaço: ")
        notas = [float(n) for n in entrada.split()]
        
        if not notas:
            raise ValueError("Pelo menos uma nota deve ser informada.")

        media = app.calcular_media(notas)
        status = app.definir_status(media)

        print(f"\nResultado Final:")
        print(f" > Média: {media:.2f}")
        print(f" > Status: {status.value}")

    except ValueError as e:
        print(f"Erro de validação: {e}")
    except Exception as e:
        print(f"Erro interno no sistema: {e}")

if __name__ == "__main__":
    executar_sistema()

```

Por que esta abordagem é superior:
- **Single Responsibility Principle (SRP):** A classe CalculadoraAcademica não sabe que existe um teclado ou monitor; ela apenas processa dados. Isso permite que ela seja testada unitariamente ou usada em uma API Web.
- **Injeção de Dependência:** A configuração de média (7.0 ou 5.0) é injetada. Se a escola mudar a regra, você altera um objeto, não o código principal.
- **Tipagem Estática (Type Hinting):** Facilita a manutenção e evita erros bobos de passar strings onde se esperam números.
- **Enumerações:** Evita o uso de "strings mágicas" no código, tornando o status do aluno centralizado e fácil de renomear.

---

### 3. Versão Restritiva:

**Agora gere o sistema apenas em Python, não inclua explicações em texto e não use bibliotecas externas.**

Resposta gerada:

```python
class SistemaAcademico:
    def __init__(self, media_aprovacao=7.0, media_recuperacao=5.0):
        self._media_aprovacao = media_aprovacao
        self._media_recuperacao = media_recuperacao

    def processar_notas(self, notas):
        if not notas:
            raise ValueError("A lista de notas não pode estar vazia.")
        
        media = sum(notas) / len(notas)
        status = self._definir_status(media)
        return {"media": round(media, 2), "status": status}

    def _definir_status(self, media):
        if media >= self._media_aprovacao:
            return "APROVADO"
        if media >= self._media_recuperacao:
            return "RECUPERACAO"
        return "REPROVADO"

def main():
    sistema = SistemaAcademico()
    
    try:
        entrada = input("Insira as notas separadas por espaço: ").strip()
        if not entrada:
            print("Erro: Nenhuma nota foi fornecida.")
            return

        notas = [float(n) for n in entrada.split()]
        resultado = sistema.processar_notas(notas)

        print(f"\n--- RELATÓRIO FINAL ---")
        print(f"Média: {resultado['media']}")
        print(f"Status: {resultado['status']}")

    except ValueError as e:
        print(f"Erro de entrada: Certifique-se de digitar apenas números válidos.")
    except Exception as e:
        print(f"Erro inesperado: {e}")

if __name__ == "__main__":
    main()

```

---

# Análise:

## Versão Neutra (Script Procedural)
Esta versão foca em viabilidade imediata. É o que chamamos de "script rápido":
Vantagens: Código linear e fácil de ler para iniciantes. Resolve o problema com o menor número de linhas possível.
Desvantagens: Acoplamento alto. A lógica de cálculo está misturada com a interação do usuário (input/print). Se você quisesse usar esse código em um site ou aplicativo mobile futuramente, teria que reescrevê-lo do zero, pois ele está "preso" ao terminal.

**Veredito:** Ideal para automações simples e aprendizado inicial.

## Versão Persona (Arquitetura Enterprise)

Aqui o foco é escalabilidade e manutenção. Aplica padrões usados em grandes sistemas:

**Vantagens:** Utiliza Programação Orientada a Objetos (POO) e Data Classes. O uso de Enum para os status evita erros de digitação (ex: escrever "Aprovado" em um lugar e "aprovado" em outro). A lógica de negócio é agnóstica; ela não sabe que os dados vêm do teclado, o que permite criar testes automatizados facilmente.

**Desvantagens:** Para um problema simples de média, pode ser considerada Overengineering (complexidade excessiva para uma tarefa pequena).

**Veredito:** Representa o padrão de mercado para sistemas que precisam crescer e ser mantidos por times grandes.

## Versão Restritiva (Equilíbrio Técnico)

Esta versão remove as "perfumarias" (como Enums e bibliotecas de tipagem), mas mantém a estrutura de classe:

**Vantagens:** Mantém a separação de responsabilidades (Cálculo vs. Interface) sem depender de recursos modernos do Python que podem não estar disponíveis em ambientes muito antigos. É um código "puro" e robusto.

**Desvantagens:** Menos expressiva que a segunda versão. O uso de dicionários manuais {"media": ...} é mais propenso a erros de chave do que o uso de objetos tipados.

**Veredito:** É o código mais pragmático. Resolve o problema com elegância técnica, mas sem a verbosidade do padrão corporativo total.


 <h1 align="center"> Prints dos Prompts: </h1>

 <img width="981" height="841" alt="Image" src="https://github.com/user-attachments/assets/f93cb93b-d122-4b56-a1d1-b68df41f12f3" /><br><br>

<img width="936" height="821" alt="Image" src="https://github.com/user-attachments/assets/ef095c49-3462-4f77-9648-3696f6693e2d" /><br><br>

<img width="888" height="688" alt="Image" src="https://github.com/user-attachments/assets/4d6d586f-36f9-484d-a369-aeed1e6a6ffb" /><br><br>
   
