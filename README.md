import urllib.request
import json

def obter_cotacoes():
    print("Conectando ao servidor de câmbio...")
    url = "https://economia.awesomeapi.com.br/last/USD-BRL,EUR-BRL"
    
    try:
        req = urllib.request.urlopen(url)
        dados = json.loads(req.read())
        
        usd = float(dados["USDBRL"]["bid"])
        eur = float(dados["EURBRL"]["bid"])
        
        print("\n--- Cotações Atuais ---")
        print(f"💵 Dólar: R$ {usd:.2f}")
        print(f"💶 Euro:  R$ {eur:.2f}")
        print("-----------------------\n")
        
    except Exception as e:
        print("Erro ao buscar dados de mercado:", e)

if __name__ == "__main__":
    obter_cotacoes()
