# 💻 Sistema Bancário 💻
### Desafio do Bootcamp Python AI Backend developer, desenvolvendo um sistema bancário.

## Código:

menu = """

[1] Depósito
[2] Saque
[3] Extrato
[0] Sair 

menu => """

saldo = 0
limite = 500
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 3
saque_minimo = 10

while True:

    opcao = input('Selecione a opção desejada: \n[1] Depósito \n[2] Saque \n[3] Extrato \n[0] Sair \n:')

    if opcao == '1':
        valor = float(input('Informe o valor para depósito: '))

        if valor > 0:
            saldo += valor

            extrato += f'Depósito: R${valor:.2f} \n'
            print('Depósito realizado com sucesso!')

        else:
            print('Opção inválida, tente novamente')
    
    elif opcao == '2':
        valor = float(input('Informe o valor do saque: '))

        saldo_insuficiente = valor > saldo

        excedeu_limite = valor > limite

        excedeu_saques = numero_saques >= LIMITE_SAQUES

        valor_invalido = valor < saque_minimo

        if saldo_insuficiente:
            print('Saldo insuficiente, tente novamente')

        elif excedeu_limite:
            print('Limite de saque insuficiente, tente novamente')

        elif excedeu_saques:
            print('Número de saques diários excedito')

        elif valor_invalido:
            print('Valor inválido, por favor tente novamente.')

        elif valor > 0:

            if valor >= 10 and valor % 10 == 0:
                saldo -= valor
                extrato += f'Saque: R${valor:.2f} \n'
                numero_saques += 1
                print(f'Saque de R${valor:.2f} realizado com sucesso!')
                
            else:
                print('Opção inválida, tente novamente')

    elif opcao == '3':

        print('\n########## EXTRATO ##########')
        print('\nNão foram realizadas movimentações.' if not extrato else extrato)
        print(f'\nSaldo: R$ {saldo:.2f}')
        print('#################################')

    elif opcao == '0':
        break

    else:
        print('Opção inválida, por favor tente novamente.')









 
