# ESP32 MPU6050 Web Server

Este projeto utiliza o **ESP32** com o sensor **MPU6050** para coletar dados de giroscópio, acelerômetro e temperatura, e os exibe em tempo real em uma página web. O servidor web é acessado via **Wi-Fi** e os dados do sensor são enviados para a página web utilizando **Server-Sent Events (SSE)**.

## Requisitos

- **ESP32**: microcontrolador para rodar o código.
- **MPU6050**: sensor para detectar movimento e temperatura.
- **Wi-Fi**: para conectar o ESP32 à rede e acessar o servidor web.
- **SPIFFS**: sistema de arquivos usado para armazenar a página web no ESP32.

## Bibliotecas Utilizadas

- [WiFi](https://www.arduino.cc/en/Reference/WiFi): Para conectar o ESP32 à rede Wi-Fi.
- [ESPAsyncWebServer](https://github.com/me-no-dev/ESPAsyncWebServer): Para criar o servidor web assíncrono.
- [AsyncTCP](https://github.com/me-no-dev/AsyncTCP): Para comunicação TCP assíncrona.
- [Adafruit_MPU6050](https://github.com/adafruit/Adafruit_MPU6050): Para interface com o sensor MPU6050.
- [Arduino_JSON](https://github.com/arduino-libraries/Arduino_JSON): Para manipulação de dados JSON.
- [SPIFFS](https://github.com/esp8266/Arduino/tree/master/libraries/SPIFFS): Sistema de arquivos utilizado para armazenar arquivos como HTML.

## Instalação

### Passo 1: Configurar o Ambiente de Desenvolvimento

1. Instale o **Arduino IDE** ou utilize o **PlatformIO**.
2. Adicione a placa **ESP32** ao seu ambiente de desenvolvimento (se estiver utilizando o Arduino IDE, você pode adicionar a placa no Gerenciador de Placas).
3. Instale as bibliotecas mencionadas acima (você pode usar o **Gerenciador de Bibliotecas** no Arduino IDE ou adicionar manualmente via PlatformIO).

### Passo 2: Subir o Código para o ESP32

1. Conecte o ESP32 ao seu computador via cabo USB.
2. Abra o código no Arduino IDE ou em outro editor de sua preferência.
3. No código, substitua as variáveis `ssid` e `password` com suas credenciais de Wi-Fi:

    ```cpp
    const char* ssid = "SuaRedeWiFi";
    const char* password = "SuaSenhaWiFi";
    ```

4. Se você ainda não tiver o arquivo `index.html` no diretório `SPIFFS`, crie o arquivo com o conteúdo HTML que deseja mostrar em seu servidor web.

### Passo 3: Carregar o Código

Carregue o código para o ESP32 e abra o monitor serial. O ESP32 se conectará à rede Wi-Fi e você verá o endereço IP do dispositivo no monitor serial.

### Passo 4: Acessar o Servidor Web

Após o ESP32 se conectar à sua rede Wi-Fi, você pode acessar o servidor web em um navegador. Digite o IP mostrado no monitor serial, por exemplo:

http://192.168.1.100


Na página web, você poderá visualizar os dados de giroscópio, acelerômetro e temperatura em tempo real.

## Funcionalidades

- **Sensor de Giroscópio (Gyro)**: Coleta e exibe as leituras dos eixos X, Y, Z.
- **Acelerômetro (Accelerometer)**: Coleta e exibe as leituras dos eixos X, Y, Z.
- **Temperatura (Temperature)**: Exibe a temperatura do sensor MPU6050.
- **Resetar Leituras**: Você pode resetar individualmente as leituras dos eixos do giroscópio (`/resetX`, `/resetY`, `/resetZ`) ou todas as leituras com o comando `/reset`.

## Como Funciona

1. O ESP32 coleta os dados do sensor MPU6050 a cada intervalo de tempo e os envia para o servidor web via **Server-Sent Events**.
2. O servidor web serve os dados do sensor em tempo real no formato JSON para o navegador.
3. A página HTML recebe e exibe os dados de giroscópio, acelerômetro e temperatura ao vivo.

## Funcionalidades de Resets

- **/reset**: Reseta todas as leituras dos sensores (giroscópio, acelerômetro, temperatura).
- **/resetX**: Reseta a leitura do eixo X do giroscópio.
- **/resetY**: Reseta a leitura do eixo Y do giroscópio.
- **/resetZ**: Reseta a leitura do eixo Z do giroscópio.

## Estrutura do Projeto

- `index.html`: Arquivo HTML servido pelo ESP32 contendo a interface do servidor web.
- `SPIFFS`: Sistema de arquivos onde o conteúdo está armazenado.
- `MPU6050.ino`: Código fonte que lida com a coleta de dados dos sensores e o servidor web.

## Contribuindo

1. Faça um fork deste repositório.
2. Crie uma nova branch (`git checkout -b feature/xyz`).
3. Faça suas alterações e commite (`git commit -am 'Adiciona nova feature'`).
4. Faça push para a sua branch (`git push origin feature/xyz`).
5. Abra um pull request.

## Licença

Este projeto está licenciado sob a [MIT License](LICENSE).

