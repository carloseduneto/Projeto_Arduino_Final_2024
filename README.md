# 🤖 **Robô Seguidor de Linha – Tutorial Passo a Passo** 🚗  
_Carlos Eduardo Neto, Felipe Passagem e Hiago Rossi_  


## 🛠️ **Introdução**  

O Arduino é uma plataforma super popular para prototipagem eletrônica devido à sua **facilidade de uso** e flexibilidade. Nesse tutorial, vamos criar um robô seguidor de linha 🚶‍♂️ e explorar na prática como essas máquinas, amplamente usadas em fábricas 🏭, operam.

### O que é um robô seguidor de linha?  
Um seguidor de linha é um robô capaz de percorrer trajetos baseados em marcações no chão, utilizando sensores que captam contrastes de cor 🎨 e enviam essas informações ao microcontrolador. Com lógica de programação 🔧, o robô "decide" o caminho a seguir.


## 🧩 **Montagem do Robô**  

### 📋 **Materiais Necessários:**  
- 🟦 1x Uno R3 + Cabo USB  
- 🏎️ 1x Ponte H L298N  
- 🚗 1x Kit Chassi 2WD  
- 👀 2x Sensores Infravermelhos  
- ⚙️ 20x Jumpers (Macho/Macho e Macho/Fêmea)  
- 🔌 1x Conector de energia
- 🛠️ Chave Philips

### 🔧 **Etapas de Montagem:**  
1️⃣ Fixe os pilares de suporte 🛠️.  
2️⃣ Parafuse a roda boba 🔩.  
3️⃣ Monte os suportes e o interruptor 🏗️.
4️⃣ Conecte os sensores 📡 ao chassi.  


## 💻 **Programação**  

Após montar o hardware, configure o Arduino com o código abaixo:  

```cpp
//Definição dos pinos de controle do motor
#define M1 9 // Pino_Velocidade 1º Motor ( 0 a 255)_ Porta IN2 ponte H;
#define M2 11 //Pino_Velocidade 2º Motor ( 0 a 255) _ Porta IN4 ponte H;
#define dir1 8 //Pino_Direção do 1º Motor: Para frente / Para trás (HIGH ou LOW)_ porta IN1 ponte H;
#define dir2 10 //Pino_Direção do 2º Motor: Para frente / Para trás (HIGH ou LOW)_ porta IN3 ponte H;

//Definição dos pinos dos sensores
#define pin_S1 7
#define pin_S2 6
bool Sensor1 = 0;
bool Sensor2 = 0;

//variável responsável por controlar a velocidade dos motores
int velocidade = 100;

void setup(){
//Setamos os pinos de controle dos motores como saída
pinMode(M1, OUTPUT);
pinMode(M2, OUTPUT);
pinMode(dir1, OUTPUT);
pinMode(dir2, OUTPUT);

//Setamos a direção inicial do motor como 0, isso fará com que ambos os motores girem para frente
digitalWrite(dir1, LOW); //era LOW
digitalWrite(dir2, LOW); //era LOW

//Setamos os pinos dos sensores como entrada
pinMode(pin_S1, INPUT);
pinMode(pin_S2, INPUT);
}

void loop(){
//Neste processo armazenamos o valor lido pelo sensor na variável que armazena tais dados.
Sensor1 = digitalRead(pin_S1);
Sensor2 = digitalRead(pin_S2);

//Aqui está toda a lógica de comportamento do robô: Para a cor branca atribuímos o valor 0 e, para a cor preta, o valor 1.
if((Sensor1 == 0) && (Sensor2 == 0)){ // Se detectar na extremidade das faixas duas cores brancas
analogWrite(M1, velocidade); // Ambos motores ligam na mesma velocidade
analogWrite(M2, velocidade);
}

if((Sensor1 == 1) && (Sensor2 == 0)){ // Se detectar um lado preto e o outro branco
analogWrite(M1, 0); // O motor 1 desliga
analogWrite(M2, velocidade); // O motor 2 fica ligado, fazendo assim o carrinho virar
}

if((Sensor1 == 0) && (Sensor2 == 1)){ // Se detectar um lado branco e o outro preto
analogWrite(M1, velocidade); //O motor 1 fica ligado
analogWrite(M2, 0); // O motor 2 desliga, fazendo assim o carrinho virar no outro sentido
}

}
```


## 📹 **Resultado Final**  
 <a href="https://youtu.be/tIgl5hv3SBc?si=0pmizhn4D5mV7-Ej">Demonstração do projeto</a> 


## 📎 **Referência** 
Robô Seguidor de Linha - Tutorial Completo. Blog Eletrogate. Disponível em: <https://blog.eletrogate.com/robo-seguidor-de-linha-tutorial-completo/>.
