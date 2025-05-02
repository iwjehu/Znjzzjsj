import random
import time

frutas = ['Fogo', 'Gelo', 'Luz', 'Escuridão', 'Chama', 'Gravidade']
inimigos = ['Marinheiro', 'Bandido', 'Chefão da Ilha', 'Pirata Revoltado']

personagem = {
    'nome': '',
    'nível': 1,
    'vida': 100,
    'fruta': random.choice(frutas)
}

def batalha():
    inimigo = random.choice(inimigos)
    print(f"\nVocê encontrou um {inimigo}!")
    vida_inimigo = random.randint(50, 120)

    while personagem['vida'] > 0 and vida_inimigo > 0:
        dano = random.randint(10, 30)
        print(f"Você usou a fruta {personagem['fruta']} e causou {dano} de dano!")
        vida_inimigo -= dano
        time.sleep(1)

        if vida_inimigo <= 0:
            print(f"Você derrotou o {inimigo}!")
            personagem['nível'] += 1
            personagem['vida'] = 100
            print(f"Subiu para o nível {personagem['nível']}!")
            break

        dano_inimigo = random.randint(5, 25)
        personagem['vida'] -= dano_inimigo
        print(f"O {inimigo} causou {dano_inimigo} de dano! Sua vida: {personagem['vida']}")
        time.sleep(1)

    if personagem['vida'] <= 0:
        print("Você foi derrotado. Fim de jogo.")

def jogar():
    personagem['nome'] = input("Digite o nome do seu personagem: ")
    print(f"\nBem-vindo, {personagem['nome']}!")
    print(f"Sua fruta inicial é: {personagem['fruta']}")

    while personagem['vida'] > 0:
        escolha = input("\nDeseja batalhar? (s/n): ").lower()
        if escolha == 's':
            batalha()
        else:
            print("Saindo do jogo. Até logo!")
            break

jogar()
