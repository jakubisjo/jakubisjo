# Tento kód zaisťuje komunikáciu medzi backendom a AI modelom
# Používame OpenAI API na získanie odpovedí z modelu ChatGPT

import openai  # Import OpenAI knižnice pre prácu s API

# Inicializujeme kľúč API (uisti sa, že tento kľúč nie je verejne dostupný)
openai.api_key = 'tvoj_api_kluc'

def ziskat_odpoved(prompt):
    """
    Táto funkcia posiela textový prompt na OpenAI API a vracia odpoveď.
    :param prompt: Text, ktorý odosielame modelu
    :return: Odpoveď od modelu
    """
    try:
        response = openai.Completion.create(
            engine="text-davinci-003",  # Zvoliť konkrétny model (v tomto prípade ChatGPT)
            prompt=prompt,
            max_tokens=100  # Nastaviť maximálny počet tokenov (dĺžka odpovede)
        )
        return response.choices[0].text.strip()
    except Exception as e:
        print(f"Chyba pri volaní API: {e}")
        return "Ospravedlňujeme sa, nastala chyba."

# Príklad použitia funkcie
prompt = "Ahoj, ako sa máš?"
odpoved = ziskat_odpoved(prompt)
print(odpoved)  # Výstup: Odpoveď od AI modelu
