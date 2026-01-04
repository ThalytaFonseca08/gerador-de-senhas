import random
import string
import os

def gerar_senha(tamanho, incluir_maiusculas, incluir_numeros, incluir_simbolos):
    caracteres = string.ascii_lowercase
    if incluir_maiusculas:
        caracteres += string.ascii_uppercase
    if incluir_numeros:
        caracteres += string.digits
    if incluir_simbolos:
        caracteres += string.punctuation
    senha = ''.join(random.choice(caracteres) for _ in range(tamanho))
    return senha

def executar_projeto():
    os.system('cls' if os.name == 'nt' else 'clear')
    print("========================================")
    print("       GERADOR DE SENHAS AUTOMÁTICO     ")
    print("========================================\n")

    try:
        comprimento = int(input("Digite o tamanho da senha (recomendado: 12 ou +): "))
        if comprimento < 4:
            print("\nErro: Para sua segurança, use no mínimo 4 caracteres.")
        else:
            maius = input("Incluir letras MAIÚSCULAS? (s/n): ").strip().lower() == 's'
            numeros = input("Incluir NÚMEROS? (s/n): ").strip().lower() == 's'
            simbolos = input("Incluir SÍMBOLOS (!@#$)? (s/n): ").strip().lower() == 's'

            senha_final = gerar_senha(comprimento, maius, numeros, simbolos)

            print("\n" + "-"*40)
            print(f"SUA SENHA GERADA: {senha_final}")
            print("-"*40)

    except ValueError:
        print("\nErro: Por favor, digite apenas números.")

if __name__ == "__main__":
    executar_projeto()
    # ESTA LINHA ABAIXO É A QUE IMPEDE A JANELA DE FECHAR:
    input("\nPrograma finalizado. Pressione Enter para fechar esta janela...")
