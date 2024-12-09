# Projeto_Arduino_Final_2024

Robô Seguidor de Linha - Tutorial Completo. Blog Eletrogate. Disponível em: <https://blog.eletrogate.com/robo-seguidor-de-linha-tutorial-completo/>.

# 🤖 **Robô Seguidor de Linha – Tutorial Passo a Passo** 🚗  
_Eletrogate - Publicado em 15/07/2020 | Atualizado em: 25/05/2023_  

---

## 🛠️ **Introdução**  

O Arduino é uma plataforma super popular para prototipagem eletrônica devido à sua **facilidade de uso** e flexibilidade. Nesse tutorial, vamos criar um robô seguidor de linha 🚶‍♂️ e explorar na prática como essas máquinas, amplamente usadas em fábricas 🏭, operam.

### O que é um robô seguidor de linha?  
Um seguidor de linha é um robô capaz de percorrer trajetos baseados em marcações no chão, utilizando sensores que captam contrastes de cor 🎨 e enviam essas informações ao microcontrolador. Com lógica de programação 🔧, o robô "decide" o caminho a seguir.

---

## 🧩 **Montagem do Robô**  

### 📋 **Materiais Necessários:**  
- 🟦 1x Uno R3 + Cabo USB  
- 🏎️ 1x Ponte H L298N  
- 🚗 1x Kit Chassi 2WD  
- 🔋 1x Adaptador Bateria 9V  
- 👀 2x Sensores Infravermelhos  
- ⚙️ 20x Jumpers (Macho/Macho e Macho/Fêmea)  
- 🔌 1x Bateria 9V e 4x Pilhas AA  
- 🛠️ Chave Philips e Ferro de Solda  

### 🔧 **Etapas de Montagem:**  
1️⃣ Fixe os pilares de suporte 🛠️.  
2️⃣ Parafuse a roda boba 🔩.  
3️⃣ Solde os fios nos motores 🔗.  
4️⃣ Monte os suportes e o interruptor 🏗️.  
5️⃣ Conecte os sensores 📡 ao chassi.  

---

## 💻 **Programação**  

Após montar o hardware, configure o Arduino com o código abaixo:  

```cpp
#define M1 9  
#define M2 11  
#define dir1 8  
#define dir2 10  
#define pin_S1 7  
#define pin_S2 6  
int velocidade = 150;  

void setup() {  
  pinMode(M1, OUTPUT); pinMode(M2, OUTPUT);  
  pinMode(dir1, OUTPUT); pinMode(dir2, OUTPUT);  
  pinMode(pin_S1, INPUT); pinMode(pin_S2, INPUT);  
}  

void loop() {  
  bool Sensor1 = digitalRead(pin_S1);  
  bool Sensor2 = digitalRead(pin_S2);  

  if (Sensor1 == 0 && Sensor2 == 0) {  
    analogWrite(M1, velocidade);  
    analogWrite(M2, velocidade);  
  } else if (Sensor1 == 1 && Sensor2 == 0) {  
    analogWrite(M1, 0); analogWrite(M2, velocidade);  
  } else if (Sensor1 == 0 && Sensor2 == 1) {  
    analogWrite(M1, velocidade); analogWrite(M2, 0);  
  }  
}

```

## 📝 **Dica**  
Ajuste o valor da variável `velocidade` no código para alterar a rapidez do robô (intervalo: 0-255).  

---

## 🎉 **Resultado Final**  
Depois de montar e programar, teste seu robô criando um trajeto com fita preta em uma superfície branca 🏁. Assista ao robô em ação 🚀!  

---

## 🙌 **Conclusão**  
Com o Arduino e alguns componentes básicos, construímos um robô funcional para aprender sobre robótica e automação industrial 🏗️.  

---

## 📸 **Compartilhe!**  
Mostre o resultado do seu projeto nas redes sociais e nos marque no Instagram: [@eletrogate](https://instagram.com/eletrogate).  

---
