import telebot
import schedule
import time
import datetime

# === CONFIGURAÇÕES ===
TOKEN = "8078262984:AAEONQrGTa4xeKRIAPb7YQXMHF-1QAl1BBU"
CHAT_ID = "7299432830"  # Teu chat_id (já me deste acima)

bot = telebot.TeleBot(TOKEN)

# Função para enviar mensagem
def enviar_pick():
    hoje = datetime.date.today()
    amanha = hoje + datetime.timedelta(days=1)

    mensagem = f"""
📊 *Palpite Automático 2.0 ODD*

📅 Jogo selecionado para o dia: {amanha.strftime("%d/%m/%Y")}
🏟️ Liga analisada: Premier League / Primeira Liga
🎯 Melhor aposta sugerida: Odd @2.00

⚡ Gestão de banca recomendada:
- Kelly 1/4
- Kelly Completo
- Stake fixa 50%
- Valor fixo disponível

🤖 By Palpites2ODDBOT
"""
    bot.send_message(CHAT_ID, mensagem, parse_mode="Markdown")

# Agenda para rodar só de segunda a sexta às 20h
schedule.every().monday.at("20:00").do(enviar_pick)
schedule.every().tuesday.at("20:00").do(enviar_pick)
schedule.every().wednesday.at("20:00").do(enviar_pick)
schedule.every().thursday.at("20:00").do(enviar_pick)
schedule.every().friday.at("20:00").do(enviar_pick)

# Loop infinito
while True:
    schedule.run_pending()
    time.sleep(30)
    python bot.py
