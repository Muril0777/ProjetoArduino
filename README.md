# ProjetoArduino

Descrição do Projeto com Arduino

Este projeto foi desenvolvido com o objetivo de criar um sistema simples de monitoramento de luminosidade, utilizando componentes eletrônicos básicos controlados por uma placa Arduino Uno. A proposta principal é simular uma situação onde a variação de luz em um ambiente ativa diferentes sinais visuais e sonoros.

Componentes Utilizados:

Arduino Uno: Microcontrolador responsável por processar os dados recebidos do sensor de luz e acionar os LEDs e o buzzer conforme a lógica programada.

Protoboard (placa de ensaio): Facilitou a montagem e a organização dos circuitos eletrônicos, permitindo ajustes durante os testes.

LEDs (verde, amarelo e vermelho): Funcionam como indicadores visuais dos níveis de luminosidade. Cada um representa uma faixa diferente de intensidade de luz.

Buzzer: Emite um som em determinadas situações, servindo como alerta sonoro complementar à sinalização por LEDs.

Sensor de luz (LDR – Light Dependent Resistor): Responsável por medir a quantidade de luz no ambiente. Seu valor de resistência muda de acordo com a luminosidade, permitindo que o Arduino interprete o ambiente e tome decisões com base nesses dados.

Resistores: Utilizados para proteger os LEDs e garantir a leitura correta do sensor LDR.

Integrantes: 
Ana Luiza           RM: 592098
Enzo Ramos          RM: 565832
João Verardo        RM: 563700
Lucca Fernandes     RM: 563961
Murilo Mendes       RM: 564193

Link do projeto: https://www.tinkercad.com/things/6KPjsMZnq5p/editel?returnTo=%2Fdashboard%2Fdesigns%2Fcircuits&sharecode=-x2rOfNU4enoCi3nXruKCMkzlsshzV2Upze0c003x9E

Código do projeto:


const int pinoSensorLuz = A0;
const int ledVerde = 2;
const int ledAmarelo = 3;
const int ledVermelho = 4;
const int buzina = 5;


const int limiarBaixo = 500;   
const int limiarMedio = 800;   

void setup() {
  pinMode(ledVerde, OUTPUT);
  pinMode(ledAmarelo, OUTPUT);
  pinMode(ledVermelho, OUTPUT);
  pinMode(buzina, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  int leituraLuz = analogRead(pinoSensorLuz);
  Serial.println(leituraLuz);

  
  digitalWrite(ledVerde, LOW);
  digitalWrite(ledAmarelo, LOW);
  digitalWrite(ledVermelho, LOW);
  digitalWrite(buzina, LOW);

  if (leituraLuz < limiarBaixo) {
    
    digitalWrite(ledVerde, HIGH);
  }
  else if (leituraLuz < limiarMedio) {
    
    digitalWrite(ledAmarelo, HIGH);
  }
  else {
    
    digitalWrite(ledVermelho, HIGH);
    
    digitalWrite(buzina, HIGH);
    delay(3000);
    digitalWrite(buzina, LOW);
    delay(2000);
  }

  delay(1000); 
}

