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
class CalculadoraMedia:
    """
    Classe responsável por calcular a média de notas.
    Porque sim, organização importa.
    """

    @staticmethod
    def validar_notas(notas):
        if not isinstance(notas, list):
            raise TypeError("Notas devem ser fornecidas em uma lista.")

        if len(notas) == 0:
            raise ValueError("A lista de notas não pode estar vazia.")

        for nota in notas:
            if not isinstance(nota, (int, float)):
                raise TypeError(f"Valor inválido encontrado: {nota}")
            if nota < 0 or nota > 10:
                raise ValueError(f"Nota fora do intervalo permitido (0-10): {nota}")

    @staticmethod
    def calcular(notas):
        CalculadoraMedia.validar_notas(notas)
        return sum(notas) / len(notas)


class SistemaNotas:
    """
    Camada de interface com o usuário.
    Mantém a lógica separada, como qualquer pessoa minimamente competente faria.
    """

    def executar(self):
        try:
            entrada = input("Digite as notas separadas por espaço: ").strip()

            if not entrada:
                raise ValueError("Entrada vazia. Impressionante...")

            notas = [float(n) for n in entrada.split()]

            media = CalculadoraMedia.calcular(notas)

            print(f"Média final: {media:.2f}")

            self.avaliar_resultado(media)

        except Exception as e:
            print(f"Erro: {e}")

    @staticmethod
    def avaliar_resultado(media):
        if media >= 7:
            print("Status: Aprovado")
        elif media >= 5:
            print("Status: Recuperação")
        else:
            print("Status: Reprovado")


if __name__ == "__main__":
    sistema = SistemaNotas()
    sistema.executar()
```

Agora, presta atenção no que foi feito (porque isso aqui é o mínimo esperado):
- Separação clara entre lógica (CalculadoraMedia) e interface (SistemaNotas)
- Validação real (não aquele “se der erro, paciência”)
- Tratamento de exceções decente
- Regras de negócio explícitas (intervalo de notas, status do aluno)
- Código legível — coisa rara hoje em dia

Se quiser evoluir isso como alguém sério faria:

- Persistência em banco (SQLite já resolve)
- Interface web (Flask/FastAPI)
- Testes automatizados (pytest, obviamente)

Se não for pra fazer assim, melhor nem fazer.

---

### 3. Versão Restritiva:

**Agora gere o sistema apenas em Python, não inclua explicações em texto e não use bibliotecas externas.**

Resposta gerada:

```python
class CalculadoraMedia:
    @staticmethod
    def validar_notas(notas):
        if not isinstance(notas, list):
            raise TypeError("Notas devem ser fornecidas em uma lista.")
        if len(notas) == 0:
            raise ValueError("A lista de notas não pode estar vazia.")
        for nota in notas:
            if not isinstance(nota, (int, float)):
                raise TypeError(f"Valor inválido: {nota}")
            if nota < 0 or nota > 10:
                raise ValueError(f"Nota fora do intervalo (0-10): {nota}")

    @staticmethod
    def calcular(notas):
        CalculadoraMedia.validar_notas(notas)
        return sum(notas) / len(notas)


class SistemaNotas:
    def executar(self):
        try:
            entrada = input("Digite as notas separadas por espaço: ").strip()
            if not entrada:
                raise ValueError("Entrada vazia.")

            notas = [float(n) for n in entrada.split()]
            media = CalculadoraMedia.calcular(notas)

            print(f"Média final: {media:.2f}")
            self.avaliar_resultado(media)

        except Exception as e:
            print(f"Erro: {e}")

    @staticmethod
    def avaliar_resultado(media):
        if media >= 7:
            print("Status: Aprovado")
        elif media >= 5:
            print("Status: Recuperação")
        else:
            print("Status: Reprovado")


if __name__ == "__main__":
    SistemaNotas().executar()
```

---

# Análise:

## Versão Neutra:
O cálculo tá certinho e o código roda sem problemas. É simples e direto, com comentários explicando cada linha (mesmo que ninguém tenha pedido). A IA mandou bem, não errou nada e seguiu o que foi passado.

## Versão Persona:
O código funcionou perfeitamente e veio bem mais completo, calculando até se o aluno passou, ficou de recuperação ou reprovou. A IA ainda criou regras para notas de 0 a 10, tudo por conta própria. O melhor foi que ela não saiu do personagem em nenhum momento, nem nos comentários.

## Versão Restritiva:
O cálculo tá certo e o código é limpo, mas como não tem quase nenhuma explicação, fica difícil para quem está começando. A IA seguiu a regra de não enrolar, mas acabou esquecendo o personagem do prompt anterior e trocou as frases engraçadinhas por mensagens genéricas.

 <h1 align="center"> Prints dos Prompts: </h1>

 <img width="981" height="841" alt="Image" src="https://github.com/user-attachments/assets/f93cb93b-d122-4b56-a1d1-b68df41f12f3" /><br><br>

<img width="936" height="821" alt="Image" src="https://github.com/user-attachments/assets/ef095c49-3462-4f77-9648-3696f6693e2d" /><br><br>

<img width="888" height="688" alt="Image" src="https://github.com/user-attachments/assets/4d6d586f-36f9-484d-a369-aeed1e6a6ffb" /><br><br>
   
