# 🍼 Projeto Pedido Mamadeira com ESP32 e MQTT
👥 Integrantes
Henrique Maciel Rodrigues / 559628

Igor Pereira Nociti / 560225

Luigi Bonuccelli / 560950

Pedro Paulo Sabino / 559578


🏫 Sala: 1ESPS

🌐 Links importantes
Link do projeto:https://wokwi.com/projects/430794778167271425

Link do fluxo: https://drive.google.com/file/d/17upG4X8If0Y2ILsTFLNYz_4If1Z_bGPC/view?usp=sharing

Link do vídeo demonstrativo: (se tiver, coloque aqui)

📋 Descrição do Projeto
Esse projeto utiliza um ESP32 conectado a um display LCD I2C para receber pedidos via MQTT através do aplicativo MyMQTT no celular. O sistema permite que o usuário informe o número do quarto e selecione o tipo de pedido (mamadeira, chamar médico ou pedir remédio) remotamente.

O ESP32 exibe no LCD mensagens com scroll, recebe as respostas via MQTT, e mostra uma previsão falsa de tempo para atendimento, criando um fluxo interativo de pedido dentro do hospital.

⚙️ Pré-requisitos
Você vai precisar de:

ESP32 (qualquer modelo compatível)

Display LCD 16x2 com interface I2C (pino SDA no GPIO21, SCL no GPIO22)

Aplicativo MyMQTT ou outro cliente MQTT no celular

Broker MQTT público (usamos mqtt-dashboard.com no projeto)

Fios e alimentação para o ESP32 e LCD

🔧 Instalação e Montagem
Conecte o LCD I2C ao ESP32:

SDA → GPIO 21

SCL → GPIO 22

VCC → 5V

GND → GND

Faça upload do código para o ESP32 via Arduino IDE ou plataforma equivalente.

Configure o aplicativo MyMQTT para se conectar ao broker MQTT:

Host: mqtt-dashboard.com

Porta: 1883

Sem usuário e senha (se desejar, configure)

No app, inscreva-se nos tópicos:

quarto/numero para enviar o número do quarto

pedido/acao para enviar o tipo de pedido (1, 2 ou 3)

💻 Como usar
Ao ligar, o LCD mostra a mensagem “Seja bem vindo Hospital Sabara” em scroll.

Depois pergunta “Qual o seu quarto?” e espera você enviar o número pelo MQTT no tópico quarto/numero.

Em seguida, mostra as opções de pedido (mamadeira, médico, remédio) em scroll.

Você envia o número correspondente da opção pelo tópico pedido/acao.

O LCD exibe o pedido recebido e uma previsão de tempo fictícia para atendimento.

Você pode pressionar o botão físico conectado ao GPIO5 para resetar o fluxo e fazer novo pedido.

📖 Código principal
O código está organizado para:

Manter o MQTT sempre conectado

Atualizar o LCD conforme estado (boas-vindas, perguntar quarto, scroll opções, mostrar resultado)

Receber mensagens MQTT e atualizar o fluxo sem travar o microcontrolador

Controlar o tempo dos textos usando millis() para evitar delays bloqueantes

✅ Testes realizados
Teste da conexão WiFi e MQTT com broker público

Teste de envio/recebimento de mensagens pelo app MyMQTT

Teste da atualização correta e fluida do LCD com scroll e mensagens fixas

Teste do botão para reiniciar fluxo e limpar variáveis

🧰 Tecnologias e bibliotecas
ESP32 e Arduino framework

Biblioteca LiquidCrystal_I2C para LCD

Biblioteca PubSubClient para MQTT

Aplicativo MyMQTT no smartphone

Broker MQTT público mqtt-dashboard.com
