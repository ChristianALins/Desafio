def identificar_bandeira(numero_cartao):
    prefixos = {
        "Visa": ["4"],
        "MasterCard": ["51", "52", "53", "54", "55"] + [str(i) for i in range(2221, 2721)],
        "American Express": ["34", "37"],
        "Discover": ["6011"] + [str(i) for i in range(622126, 622926)] + [str(i) for i in range(644, 650)] + ["65"]
    }

    for bandeira, lista_prefixos in prefixos.items():
        if any(numero_cartao.startswith(prefixo) for prefixo in lista_prefixos):
            return bandeira

    return "Bandeira desconhecida"

# Teste
numero_teste = "4532756278208291"
print(identificar_bandeira(numero_teste))  # Saída esperada: Visa
