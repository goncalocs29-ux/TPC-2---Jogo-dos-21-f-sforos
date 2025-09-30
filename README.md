# TPC-2---Jogo-dos-21-fosforos
print("Bem-vindo ao jogo dos 21 fósforos. Utilizador vs. Computador. Quem tirar o último fósforo perde!")
print("Regras: tira 1 a 4 fósforos. Quem tirar o último perde.")

def jogo_21():
    fosforos = 21

    escolha = ""
    while escolha not in ("1","2"):
      #quando for escolher se o utilizador é o primeiro ou segundo a jogar, o programa só correrá o restante código se a resposta for "1" ou "2"
        escolha = input("Queres ser o primeiro a jogar ou o segundo?")

    utilizador = (escolha == "1")

    if utilizador:
        #O utilizador joga primeiro.
        while fosforos > 0:
            print("Fósforos restantes:", fosforos)
            max_tirar = fosforos if fosforos < 4 else 4
            jog = input(f"É a tua vez de jogar. Retiras (1-{max_tirar}): ")
            jog = int(jog)
            if jog < 1 or jog > max_tirar:
              #jog está entre 1 e 4
                print("Não aceite. Tenta de novo.")
                continue

            fosforos = fosforos - jog
            if fosforos <= 0:
                print("Tiraste o último fósforo. Perdes-te.")
                break

            comp = 5 - jog
            if comp > fosforos:
                comp = fosforos if fosforos < 4 else 4
            print("O computador tira ", comp)
            fosforos = fosforos - comp
            if fosforos <= 0:
                print("O computador tirou o último fósforo. Perdeu.")
                break

    else:
        utilizador = (escolha == "2")
        #O utilizador joga em segundo; se cometer erro, perde imediatamente.
        while fosforos > 0:
        # Turno do computador (primeiro a jogar)
          max_comp = fosforos if fosforos < 4 else 4
        #Escolhe entre 1 e 4 de forma aleatória
          comp = (fosforos % 4) + 1
          print("O computador tira", comp)
          fosforos = fosforos - comp
          if fosforos <= 0:
              print("O computador tirou o último fósforo. Perdeu.")
              break

        #Vez do utilizador
          esperado = 5 - comp
          max_tirar = fosforos if fosforos < 4 else 4
          jog = input(f"Fósforos restantes: {fosforos}. Quantos tiras (1-{max_tirar})? ")
          jog = int(jog)

          if jog < 1 or jog > max_tirar:
              print("Movimento inválido. Erro de raciocínio. O computador ganhou.")
              break

          if jog != esperado:
              print(f"Erro de raciocínio: uma boa resposta pode ser {esperado}.")
              print("O computador ganhou.")
              break

          fosforos = fosforos - jog
          if fosforos <= 0:
              print("Tiraste o último fósforo. Perdes-te.")
              break

#Iniciar o jogo
jogo_21()
