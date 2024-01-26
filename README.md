import pyautogui
import time

pyautogui.PAUSE = 2

#abrir o navegador
pyautogui.press("win")
pyautogui.write("chrome")
pyautogui.press("enter")

#entrar no sistema da empresa
time.sleep(3)
pyautogui.write("https://dlp.hashtagtreinamentos.com/python/intensivao/login")
pyautogui.press("enter")

#fazer o login
time.sleep(5)
pyautogui.click(x=428, y=376)
pyautogui.write("marcoscorsi@hotmail.com")
pyautogui.press("tab")
pyautogui.write("250910")
pyautogui.press("tab")
pyautogui.press("enter")


#importar a base de dados
import pandas
tabela = pandas.read_csv("produtos.csv")

#cadastrar os produtos
time.sleep(3)
for linha in tabela.index:
    #cadastrar código
    pyautogui.click(x=437, y=261)
    pyautogui.write(tabela.loc[linha, "codigo"])

    #cadastrar a marca do produto
    pyautogui.press("tab")
    pyautogui.write(tabela.loc[linha, "marca"])

    #cadastrar o tipo do produto
    pyautogui.press("tab")
    pyautogui.write(tabela.loc[linha, "tipo"])

    #cadastrar a categoria do produto
    pyautogui.press("tab")
    pyautogui.write(str(tabela.loc[linha, "categoria"]))

    #cadastrar o preço unitário do produto
    pyautogui.press("tab")
    pyautogui.write(str(tabela.loc[linha, "preco_unitario"]))

    #cadastrar o custo do produto
    pyautogui.press("tab")
    pyautogui.write(str(tabela.loc[linha, "custo"]))

    #cadastrar a obs
    pyautogui.press("tab")
    obs = tabela.loc[linha, "obs"]
    if not pandas.isna(obs):
        pyautogui.write(obs)
    
    #cadastrar o produto
    pyautogui.press("tab")
    pyautogui.press("enter")

    #fazer a mesma tarefa até acabar a lista
    time.sleep(1)
    pyautogui.press("Pageup")
