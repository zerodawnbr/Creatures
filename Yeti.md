<p align="center"> <img src="https://github.com/zerodawnbr/zerodawntoolbox/blob/main/imgs/banner.jpg" alt="Banner Zero Dawn"> </p>

![badge1](https://img.shields.io/badge/DayZ-YETI-darkred?style=for-the-badge&logo=steam)
![badge2](https://img.shields.io/badge/Version-1.0-blue?style=for-the-badge)
![badge3](https://img.shields.io/badge/Status-Stable-brightgreen?style=for-the-badge)
![badge4](https://img.shields.io/badge/Made%20By-ZeroDawnBR-orange?style=for-the-badge)

# ❄️ Yeti

Uma criatura colossal, sistemas avançados de processamento de caça e itens interativos de alta qualidade desenvolvidos exclusivamente para o servidor **ZeroDawnBR**. 

Este mod introduz o Yeti, acompanhado de mecânicas únicas de sobrevivência, crafting e decoração.

---

## 📖 Visão Geral

O **YETI** não é apenas uma retexturização, mas um ecossistema completo de caça. O mod implementa uma nova criatura ameaçadora baseada na hierarquia de infectados (`ZombieMaleBase`), com animações exclusivas, shaders de áudio imersivos (gritos, passos pesados, ataques) e um sistema de loot progressivo focado em extração contínua e troféus de caça.

<img src="https://github.com/zerodawnbr/Creatures/blob/main/images/yeti-empe.png" alt="Trofeu">

<img src="https://github.com/zerodawnbr/Creatures/blob/main/images/yeti-caido.png" alt="Yeti">

---

## 👹 A Criatura: Yeti

* **Classe:** `Zmb_Chernarus_Yeti`
* **Comportamento:** Hostil, rápido e letal. Possui ataques leves, pesados e de duas mãos.
* **Resistência:** Sistema de dano (`DamageZones`) altamente customizado. Exige poder de fogo tático para ser derrubado. Dano massivo necessário na cabeça e torso (Hitpoints calibrados para 10.000).
* **Áudio Dinâmico:** Integração com múltiplos `SoundSets` e `SoundShaders` para gritos, passos em diferentes terrenos (neve, terra), ataques e impactos.

---

## 🔪 Sistema de Loot e Skinning (Esfolamento)

Ao abater o Yeti, o jogador precisa usar ferramentas de corte para processar a caça. O skinning da criatura rende recursos valiosos:

* `Yeti_Carcass`: A carcaça massiva da criatura (Requer ação de fatiamento para extrair a carne).
* `Yeti_Pelt`: O couro do Yeti, item grande e pesado (Loot de Materiais).
* `Yeti_Head`: A cabeça decapitada, usada para crafting.
* `Yeti_Gut`: Vísceras do Yeti.
* `Yeti_Bone`: Ossos grandes para uso geral em sobrevivência.
* `Yeti_Meat_Drying_Rig_Kit`: Kit do suporte para pendurar carcaças.
* `Yeti_Meat_Drying_Rig`: Suporte para pendurar carcaças.
---

## 🥩 Mecânica Exclusiva: Fatiamento Contínuo

Diferente da caça padrão do DayZ, a carcaça do Yeti (`Yeti_Carcass`) é um item pesado que deve ser processado gradualmente.

* **Fatiamento (Slicing):** O jogador utiliza uma ferramenta de corte na carcaça e mantém o botão pressionado (Ação Contínua).
* **Rendimento Dinâmico:** A cada ciclo concluído, o jogador extrai 1 pedaço de carne fresca (`Yeti_Meat`).
* **Degradação:** A carcaça perde vida proporcionalmente a cada fatia extraída (ex: 15 fatias totais). Quando toda a carne é extraída, a carcaça atinge o estado *Ruined* (Arruinada) e não pode mais ser utilizada.

<img src="https://github.com/zerodawnbr/Creatures/blob/main/images/yeti-etapas-carcaca.jpg" alt="Carcaça">

<img src="https://github.com/zerodawnbr/Creatures/blob/main/images/yeti-carcaca-carnes.png" alt="Carcaça">

---

## 🛠️️ Crafting e Construção: Troféu de Parede e Tapete de Yeti e Suporte de Carcaças

Jogadores podem exibir suas proezas de caça montando um troféu decorativo do Yeti em suas bases.

### Troféu de Yeti
* **Receita (Crafting):** `Yeti_Head` (Cabeça) + `Wall_Mount` (Suporte de Madeira) = `Yeti_Head_Mounted`.
* **Deployable:** O troféu final (`Yeti_Head_Mounted`) utiliza um sistema de colocação de parede (Wall Placement), permitindo que os jogadores ajustem a distância e a rotação perfeitamente nas paredes de suas bases.

<img src="https://github.com/zerodawnbr/Creatures/blob/main/images/yeti-suporte-trofeu.png" alt="Trofeu">

### Tapete de Yeti
* A pele do Yeti vira um tapete que pode ser deixado no chão da base do jogador que o caçou ou pode ser vendido em traders
* Ao esfolar um Yeti, a pele fica disponivel, o jogador pega a pele e a posiciona no chão onde quiser.

<img src="https://github.com/zerodawnbr/Creatures/blob/main/images/yeti-partes.png" alt="Tapete de Yeti">

### Suporte de Carcaças
* **Receita (Crafting):** 10 Placas de Metal (MetalPlate) + um alicate (Pliers) você pode criar o suporte para segurar as carcaças, podedendo pendurar até 3 carcaças
* **Deployable:** Ao segurar o suporte em mãos, o jogador pode posicionar em qualquer lugar.
<img src="https://github.com/zerodawnbr/Creatures/blob/main/images/yeti-kit-suporte-carcaca.png" alt="Suporte Carcaça">
<img src="https://github.com/zerodawnbr/Creatures/blob/main/images/yeti-suporte-carcaca.png" alt="Suporte Carcaça">
---

## 🗺️ Itens Estáticos (Para Mappers / DayZ Editor)

Para administradores e criadores de mapas que desejam enriquecer o cenário (ex: museus, altares tribais, campos de caça), o mod fornece versões **estáticas** de todos os assets. Estes itens herdam de `HouseNoDestruct`, o que significa que são leves para o servidor e os jogadores não podem pegá-los ou roubá-los do cenário:

* `Static_Yeti_Statue`: Estátua do Yeti em escala real.
* `Static_Yeti_Carcass`: Carcaça estática para cenários de abate.
* `Static_Yeti_Carcass_Damaged`: Carcaça danificada estática para cenários de abate.
* `Static_Yeti_Carcass_Ruined`: Carcaça arruinada estática para cenários de abate.
* `Static_Yeti_Pelt`: Couro esticado no chão.
* `Static_Yeti_Head`: Cabeça do Yeti.
* `Static_Wall_Mount`: Suporte de madeira vazio estático.
* `Static_Yeti_Head_Mounted`: Cabeça do Yeti preso ao suporte de madeira para ser pendurado em paredes.
* `Static_Yeti_Meat_Raw`: Carne estática crua para exibição em cenários.
* `Static_Yeti_Meat_Dried`: Carne estática seca para exibição em cenários.
* `Static_Yeti_Meat_Cooked`: Carne estática cozida para exibição em cenários.
* `Static_Yeti_Meat_Drying_Rig_Kit`: Kit estatico do suporte para pendurar carcaças.
* `Static_Yeti_Meat_Drying_Rig`: Suporte estatico para pendurar carcaças.

---

## ⚠️️ COPYRIGHT E LICENÇA DE USO - ZERO DAWN BR ⚠️

**Este mod e todo o seu conteúdo são de propriedade intelectual e de uso estritamente exclusivo da comunidade ZeroDawnBR.**

Este pacote contém propriedade intelectual original (Modelos 3D ODOL, texturas `.paa`, materiais `.rvmat`, áudios e scripts Enforce). Fica terminantemente **PROIBIDO**:

1. **Repack / Re-upload:** Não é permitido reempacotar (repack), descompactar, consolidar em modpacks ou reenviar este arquivo para a Steam Workshop.
2. **Uso Não Autorizado:** Estes arquivos não podem ser executados em nenhum servidor de DayZ que não pertença oficialmente à rede ZeroDawnBR.
3. **Engenharia Reversa:** É estritamente proibido extrair modelos, áudios ou códigos para uso de terceiros.

**A infração de qualquer um dos termos resultará em:**
* Notificação imediata de quebra de direitos autorais (DMCA Takedown) junto à Valve.
* Denúncia oficial à Bohemia Interactive por violação do EULA, podendo acarretar no banimento do seu servidor da lista global e perda de licenças de monetização.

**ZeroDawnBR - Todos os direitos reservados.**
