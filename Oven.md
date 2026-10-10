# 🍳 Oven (Fogão a Gás Estático)

O **Oven** é um sistema avançado de simulação térmica e culinária para DayZ. Diferente das fogueiras padrão, este fogão opera com uma lógica de processamento independente, gestão de calor otimizada (Universal Temperature Source) e mecânicas de segurança auto-geridas para evitar desperdício de gás e explosões.

<img src="https://github.com/zerodawnbr/Modelos3D/blob/main/images/fogao-a-gas.jpg" alt="Oven">


## ⚙️ Características Físicas e Instalação

* **Classes:** `zdbr_static_fogao` e `zdbr_static_oven`.
* **Persistência:** Suporta salvamento no banco de dados (`storage_1`). Mantém o estado ligado/desligado mesmo após o restart do servidor.
* **Física:** Possui `physLayer = "item_large"`. É um objeto sólido (jogadores e veículos colidem com ele) e pesa 300kg.
* **Segurança Anti-Roubo:** Bloqueado por script. Não pode ser colocado nas mãos (`CanPutIntoHands = false`) nem guardado em mochilas ou veículos (`CanPutInCargo = false`).

---

## 🎒 Capacidade e Slots

A interface do fogão está dividida para maximizar a organização culinária:

1. **Slot de Combustível (`GasCanister`):** Aceita 1 Botijão de Gás. É impossível ligar o fogão sem ele.
2. **Grelhas de Forno (Slots de Anexo):** 
   * 3 Slots de `DirectCooking` (A, B, C)
   * 4 Slots de `Smoking` (A, B, C, D)
   * *Uso ideal: Anexar carnes diretamente para assar rapidamente.*
3. **Grade Interna:** Uma grelha com diversos slots.
   * *Uso ideal: Descongelar múltiplas latas de comida, garrafas de água ou acumular peças de carne.*

<img src="https://github.com/zerodawnbr/Modelos3D/blob/main/images/static_stove_inventory.png" alt="Oven">

> **Nota Técnica:** O script lê e cozinha simultaneamente **todos** os itens que estiverem nos Slots de Anexo e dentro da Grade Interna (Cargo). O motor ignora panelas, frigideiras e o próprio botijão de gás para evitar que sejam arruinados.

---

## Galeria

<img src="https://github.com/zerodawnbr/Modelos3D/blob/main/images/static_stove_front.png" alt="Oven">

<img src="https://github.com/zerodawnbr/Modelos3D/blob/main/images/static_stove_top.png" alt="Oven">


---

## 🔥 Como Ligar (Ignição)

1. Encaixe um **Botijão de Gás** com carga no slot correspondente.
2. Tenha uma **Caixa de Fósforos** ou um **Isqueiro** nas mãos.
3. Olhe para o fogão e mantenha pressionada a ação **"Acender Fogão"**.
   * *Custo:* A ação consome durabilidade/usos do fósforo ou isqueiro.

---

## 🥩 Tempos e Lógica de Cozimento (Cronômetros Individuais)

Cada item colocado no fogão possui o seu próprio cronômetro isolado. Você pode colocar uma carne, esperar 30 segundos, colocar outra, e ambas assarão nos seus tempos corretos.

### 🧊 1. Descongelamento Absoluto
* **Tempo:** **60 Segundos**.
* **Mecânica:** Se o item (carne ou bebida) entrar congelado, o fogão derrete o gelo e eleva a temperatura do item para 27ºC. 
* *Após descongelar, o cronômetro do item é zerado e ele passa automaticamente para a fase de cozimento.*

### 🍖 2. Assar Carnes (Raw -> Baked)
* **Tempo:** **60 Segundos**.
* **Mecânica:** Carnes cruas (e descongeladas) levam exatamente um minuto a assar na perfeição.

### ☄️ 3. Queimar Carnes (Baked -> Burnt)
* **Tempo:** **30 Segundos**.
* **Mecânica:** Se uma carne já assada for deixada no fogão, ela vira carvão em 30 segundos cravados.

### 🥫 4. Bebidas e Enlatados
* **Tempo:** **90 Segundos**.
* **Mecânica:** Latas e garrafas (após descongeladas) irão aquecer. Se forem esquecidas no fogão por mais de 1 minuto e meio, a sua vida útil (`HP`) cai para `0` e ficam **Arruinadas**.

---

## 🔊 Alertas Sonoros Inteligentes

Para evitar que a comida passe do ponto sem que o jogador perceba, o fogão possui alertas de áudio espelhados (Client-Side):
* **Som Contínuo:** Som de fritura e fervura enquanto o fogão está ativo.
* **Aviso de Fase (Chiado de Água):** **2 segundos antes** de qualquer alimento mudar de estado (ex: aos 58s de assar, ou 28s de queimar), o fogão emite um som agudo de água a chiar, avisando o jogador para retirar a comida imediatamente.

---

## 🧠 Sistema Inteligente de Desligamento (Eco-Gas)

O fogão monitoriza constantemente a grade e gere o seu próprio combustível:
1. **Fogão Vazio:** Se ligado sem nada dentro, corta o gás e desliga-se automaticamente após **20 Segundos**.
2. **Tudo Estragado:** Se **todos** os alimentos no fogão atingirem o estado Queimado ou Arruinado, o sistema aguarda **30 Segundos** de tolerância e desliga o gás para evitar desperdício. Se inserir comida nova nesse intervalo, o corte é abortado.
3. **Falta de Gás:** Desliga instantaneamente se o botijão esvaziar.

---

## 🌡️ Ambiente e Calor Corporal (Thermodynamics)

O fogão não serve apenas para cozinhar, ele funciona como um poderoso radiador térmico num raio de **2 a 5 metros**:
* **Blindagem do Botijão:** O calor da chapa sobe a 80ºC, mas o script força o botijão de gás acoplado a manter-se a 20ºC, impedindo a mecânica nativa de explosão da engine do DayZ.
* **Calor Corporal:** Jogadores ao lado do fogão recebem até **38ºC** de calor seguro (não causa hipertermia).
* **Secagem Rápida:** Roupas molhadas secam **3x mais rápido** perto do fogão ligado.
* **Descongelamento de Chão:** Qualquer item ou alimento congelado que seja atirado para o chão encostado ao fogão absorverá calor ambiente (até 80ºC) e descongelará rapidamente.
