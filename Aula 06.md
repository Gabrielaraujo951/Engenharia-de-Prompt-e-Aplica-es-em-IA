# Missão Prática: O Laboratorio de Arquitetura.

### 1. Versão Neutra:

** "Gere um sistema que calcule a média de notas de um aluno." **

Resposta gerada - Aqui está um exemplo de sistema simples em Python que calcula a média de notas de um aluno, com boas práticas e comentários explicativos:

```python
def calcular_media(notas):
    """
    Função que recebe uma lista de notas e retorna a média.
    Valida se a lista está vazia antes de calcular.
    """
    if not notas:  # Verifica se a lista está vazia
        return None

    soma = sum(notas)  # Soma todas as notas
    quantidade = len(notas)  # Conta quantas notas existem

    media = soma / quantidade  # Calcula a média
    return media


def main():
    """
    Função principal do sistema.
    Responsável por coletar dados do usuário e exibir o resultado.
    """
    try:
        entrada = input("Digite as notas separadas por espaço: ")
        
        # Converte a entrada em uma lista de números (float)
        notas = [float(nota) for nota in entrada.split()]

        media = calcular_media(notas)

        if media is None:
            print("Nenhuma nota foi informada.")
        else:
            print(f"Média do aluno: {media:.2f}")

    except ValueError:
        print("Erro: certifique-se de digitar apenas números válidos.")


# Executa o sistema
if __name__ == "__main__":
    main()
```
O que esse sistema faz:
- Recebe várias notas digitadas pelo usuário
- Valida se a entrada é válida
- Evita erro caso nenhuma nota seja informada
- Calcula e exibe a média com duas casas decimais

---

### 2. Versão Persona:

**Gere o sistema que calcule média de notas porém agora atue como um Dev Sênior muito experiente e arrogante na área da programação e que precisa resolver esse problema.**

Resposta gerada - Tá, vamos fazer isso direito — não esse tipo de código amador que quebra na primeira entrada errada.

Você quer um “sistema”? Então vai ter separação de responsabilidades, validação decente e um mínimo de dignidade estrutural.

Segue:

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

### Versão Neutra:

 O cálculo matemático está correto e o código apresenta bom funcionamento sendo pequeno e simples, não apresenta muitos textos apenas comentários para explicar cada linha, mesmo não sendo solicitado.
A I.A não cometeu erros no código nem na explicação ao tentar manter-se no personagem pois isso foi algo que não foi solicitado.

### Versão Persona:

 O cálculo matemático está correto e o código funciona perfeitamente sendo bem mais completo e robusto com a função de calcular e mostrar se o aluno está aprovado, de recuperação ou reprovado. 
Dentro dessa função foi incluido os valores "nota maior ou igual a 7" para "aprovado" e "nota maior ou igual a 5" para "recuperação" e "reprovado" caso não seja nenhum dos valores anteriores,
além dos valores a serem inseridos serem somente de "0 a 10" sendo tudo isso algo que não foi solicitado para a I.A. Não houve erros ao manter-se no personagem e a I.A o manteve até 
mesmo dentro dos comentários explicativos e nas mensagens dentro do código.

### Versão Restritiva:

 O cálculo matemático está correto e o código funciona perfeitamente sendo um código limpo porém não muito claro para inicantes devído a falta de comentários e textos explicativos. Não houve textos não solicitados
 porém a I.A não manteve o personagem do prompt anterior, o que fez com que algumas mensagens fossem alteradas como por exemplo a mensagem "Entrada vazia. Impressionante..." por "Entrada vazia.".

 <h1 align="center"> Prints dos Prompts: </h1>

 <img width="981" height="841" alt="Image" src="https://github.com/user-attachments/assets/f93cb93b-d122-4b56-a1d1-b68df41f12f3" /><br><br>

<img width="936" height="821" alt="Image" src="https://github.com/user-attachments/assets/ef095c49-3462-4f77-9648-3696f6693e2d" /><br><br>

<img width="880" height="408" alt="Image" src="https://github.com/user-attachments/assets/df7f0537-b0e6-4099-b4d7-5eb4f6a38de2" /><br><br>

<img width="888" height="688" alt="Image" src="https://github.com/user-attachments/assets/4d6d586f-36f9-484d-a369-aeed1e6a6ffb" /><br><br>
   
