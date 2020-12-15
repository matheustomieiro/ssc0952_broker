# SSC0952_BROKER

Broker destinado a disciplina de IoT

Todas as configurações presentes no item "mosquitto.conf" referem-se a diretórios da VM cedida ao time 1. Os certificados, chaves e arquivo de login, não serão disponibilizados nesse repositório por motivos de segurança, mas se encontram presentes nos paths referenciados.


# Introdução

  O MQTT é um protocolo de mensagens largamente utilizado nos dispositivos IoT. Ele tem como base a metodologia publish and subscribe. Ele implementa a estrutura de cabeçalhos, que define o tipo da mensagem, além de um payload opcional. São 14 tipos de mensagem padrão ao total.
O Mosquitto possui um socket que é aberto no dispositivo em que estará rodando o server, e ouve publishes e subscribes. Todas as configurações são feitas em um arquivo ".conf".

# Implementação

  O protocolo escolhido foi o MQTT. A implementação escolhida para o Broker é o MQTT Mosquitto, open-source, e desenvolvido pela Eclipse. Disponível através do link: https://mosquitto.org/.
  O server foi configurado em uma VM do ICMC. Não roda como um executável, mas sim, como um serviço diretamente na systemd da VM.
Isso garante que o Mosquito rode sem interrupções enquanto a VM permanecer ativa.

# Configurações
  
  Como configurações principais no projeto podemos citar:
  - Não autorizar dispositivos anônimos;
  - Definir username e password por meio de um arquivo texto, que posteriormente é criptografado pelo Mosquitto;
  - Definir tipo e arquivos de criptografia através de certificados e chave, emitidos utilizando a OpenSSL.
  
# Certificados e chave

  Através do OpenSSL, foram emitidos certificados auto-assinados (TLS) utilizando RSA como criptografia. Ao final, há dois ".crt" e um ".key" para cada cliente utilizar. Eles são necessários durante a verificação para publish ou subscribe no Broker, então, em sua ausência, a conexão é negada.
