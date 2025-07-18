import math

expressao = input('Digite uma função f(x): ')

def f(x):
    return eval(expressao, {'x': x, 'math': math, 'sin': math.sin, 'cos': math.cos,
                            'log': math.log, 'exp': math.exp, 'sqrt': math.sqrt})

a = float(input('Digite o limite inferior a: '))
b = float(input('Digite o limite superior b: '))
n = int(input('Digite o número de subintervalos (n): '))
tipo = input("Tipo da soma ('esquerda', 'direita' ou 'meio'): ").lower()

def soma_riemann(f, a, b, n, tipo='meio'):
    delta_x = (b - a) / n
    soma = 0

    for i in range(n):
        if tipo == 'esquerda':
            x = a + i * delta_x
        elif tipo == 'direita':
            x = a + (i + 1) * delta_x
        elif tipo == 'meio':
            x = a + (i + 0.5) * delta_x
        else:
            raise ValueError('Tipo inválido')

        soma += f(x) * delta_x

    return soma

resultado = soma_riemann(f, a, b, n, tipo)
print(f'\nAproximação da integral de {expressao} de {a} a {b}: {resultado:.6f}')
