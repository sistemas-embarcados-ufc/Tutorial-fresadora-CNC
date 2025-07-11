# ⚙️ Tutorial de Fresadora CNC e Software CNC USB

Este tutorial foi feito para auxiliar no uso da fresadora e CNC.
Temos o vídeo tutorial no nosso canal também! 
- [Como Utilizar a Fresadora CNC](https://youtu.be/749EiABCpNE)

## 1. 🔩 Fixação da PCI na Fresadora

* Fixe a placa, pressionando-a entre a base e os fixadores (porcas borboleta).  
  <div style="text-align: center;">
    <img src="Imagens/porca-borboleta.jpg" alt="porca-borboleta" style="max-width: 200px;">
  </div>
  * **Nota:** Existem dois apoios de fenolite para auxiliar na fixação.
* É crucial deixar uma pequena parte da placa para fora da mesa para conectar a "garra jacaré" do sensor de contato.

## 2. 📍 Configurações de Posicionamento

> **⚠️ Atenção:** Se algum sensor de fim de curso for acionado durante o posicionamento, a fresadora será bloqueada. Para desbloquear, clique nos cursores do software para liberar o sensor, desconecte e reconecte o cabo USB ao computador.

**2.1. Definir Posição de Referência (X e Y)**

* Utilize os cursores no software para mover a bandeja e a haste, definindo a posição física para a referência dos eixos X e Y.  
  <div style="text-align: center;">
    <img src="Imagens/botoes.png" alt="botoes" style="max-width: 200px;">
  </div>
* Normalmente, essa posição é definida no canto inferior esquerdo.

**2.2. Zerar os Eixos X e Y**

* Após o posicionamento, clique no botão **"Offset - Current XY"** (ícone laranja) para zerar os eixos X e Y no software.  
  <div style="text-align: center;">
    <img src="Imagens/definir-grid-offset.png" alt="definir-grid-offset" style="max-width: 200px;">
  </div>
* As posições X e Y no software devem agora exibir `0.00000`.

## 3. 📂 Carregar Arquivos Gerber

**3.1. Importar Gerber**

* Vá em `Arquivo` > `Importar Gerber`.  
  <div style="text-align: center;">
    <img src="Imagens/arquivo-gerber.jpg" alt="arquivo-gerber" style="max-width: 200px;">
  </div>
* Selecione o arquivo desejado (geralmente o `Bottom Copper` ou `B_Cu`).

**3.2. Configurações da Ferramenta**

Configure os parâmetros da ferramenta conforme a imagem do tutorial. Os principais são:  

* **Depth:** -0.0700. (Pode ser ajustado entre -0.06 e 0.08 se a broca for trocada).
* **Tool Diameter:** 0.1000. (Ajuste se o diâmetro da ponta da broca for diferente).
* **Mirror:** Marque esta opção. (Não marque se o Gerber foi gerado espelhado).
* **Depth (Drill Pads):** -1.8000. (Profundidade de furação, ajuste se necessário).

**3.3. Verificação da Origem da PCI**

* Após carregar o Gerber, verifique se a origem no software corresponde ao canto inferior esquerdo da PCI.
* Se não estiver correto, vá em `Programa` > `Trocar` > `Extensão para Zero XY` para ajustar.

## 4. 📏 Definir o Offset do Eixo Z

**4.1. Verificação do Sensor**

1. Remova os terminais do sensor dos ímãs.  
2. Toque um terminal no outro (preto e vermelho). A palavra "Sensor"
   <div style="text-align: center;">
     <img src="Imagens/tocar-terminais.png" alt="tocar-terminais" style="max-width: 200px;">
   </div>
3. deve aparecer no canto inferior esquerdo do software.  
  <div style="text-align: center;">
    <img src="Imagens/sensor-tela.png" alt="sensor-tela" style="max-width: 200px;">
  </div>

**4.2. Conectar o Sensor**

* Conecte o terminal preto à broca e o vermelho à placa.  
  <div style="text-align: center;">
    <img src="Imagens/terminais-postos.jpg" alt="terminais-postos" style="max-width: 200px;">
  </div>

**4.3. Posicionar a Fresadora**

* Use os cursores para mover a fresadora para o centro da PCI.

**4.4. Definir o Offset Z**

* No menu, acesse `Máquina` > `Capture Measure Points` > `Measure` > `Measure Grid Z Offset`.  
  <div style="text-align: center;">
    <img src="Imagens/capturar-e-medir-pontos.png" alt="capturar-e-medir-pontos" style="max-width: 200px;">
  </div>

**4.5. Retornar à Posição Zero**

* Clique no **ícone verde** para retornar a fresadora à posição XY 0.  
* **Importante:** Mantenha as "garras jacaré" conectadas à broca e à placa.

## 5. 📐 Medição do Desbalanceamento (Grid Z)

**5.1. Configurar o Grid**

1. Verifique as dimensões da sua placa na aba "Program".
2. Acesse `Máquina` > `Capture & Measure Points` > `Measure` > `Set Grid`.  
3. Na janela "Tool Sensor", configure o seguinte:
    * **Height:** 0.0.
    * **Retract:** 5.0.
    * **Return Distance:** 5.0.
    * **Size (X e Y):** Insira as dimensões da sua PCI (ex: X=80, Y=50).
    * **Count (X e Y):** Defina a quantidade de pontos de medição (ex: X=8, Y=5).
    * Clique nas setas `<` para definir automaticamente a distância (`Length`) entre os pontos.
  <div style="text-align: center;">
    <img src="Imagens/janela-tool-sensor.png" alt="janela-tool-sensor" style="max-width: 200px;">
  </div>

**5.2. Medir o Grid Z**

* Acesse `Máquina` > `Capture & Measure Points` > `Measure` > `Measure Grid Z`.  
  <div style="text-align: center;">
    <img src="Imagens/capturar-e-medir-pontos.png" alt="capturar-e-medir-pontos" style="max-width: 200px;">
  </div>
* Aguarde a fresadora medir todos os pontos.

**5.3. Desconectar o Sensor**

* Desconecte o sensor da placa e da broca e retorne os terminais aos seus suportes com ímãs.
  <div style="text-align: center;">
    <img src="Imagens/sensores-desconectados.png" alt="sensores-desconectados" style="max-width: 200px;">
  </div>

**5.4. Aplicar a Correção (Warp)**

> **⚠️ Cuidado:** Preste atenção para não confundir os menus. Siga as instruções atentamente.

1. Vá em `Programa` > `Advanced` > `Warp`.  
   <div style="text-align: center;">
     <img src="Imagens/janela-warp.png" alt="janela-warp" style="max-width: 200px;">
   </div>
2. Verifique se o número de pontos na janela "Warp" corresponde ao calculado (ex: (8+1)x(5+1) = 54).
3. Clique em "OK".

**5.5. Observar o Resultado**

* Clique no botão de "Vista Frontal".  
  <div style="text-align: center;">
    <img src="Imagens/vista-frontal.png" alt="vista-frontal" style="max-width: 200px;">
  </div>
* Você deverá ver as linhas brancas que representam o G-code com um desnivelamento, acompanhando a superfície da placa. Se o desnivelamento foi aplicado, a placa está pronta.

## 6. ▶️ Iniciar a Fresagem

**6.1. Selecionar Ponto de Início**

* No painel de código G à direita, encontre e selecione a linha que contém a palavra `(Isolation)`.
  <div style="text-align: center;">
    <img src="Imagens/isolation-menu.png" alt="isolation-menu" style="max-width: 200px;">
  </div>

**6.2. Iniciar o Processo**

* Vá em `Máquina` > `Start From Selected Line`.
  <div style="text-align: center;">
    <img src="Imagens/start-from-select-line.png" alt="start-from-select-line" style="max-width: 200px;">
  </div>

**6.3. Confirmação e Monitoramento**

* Uma janela de pausa aparecerá, clique em "Continuar".
* **🚨 Importante:** Mantenha o cursor do mouse sobre o botão **"Parar"** durante a fresagem. Em caso de qualquer problema, clique imediatamente em "Parar" e, em seguida, no botão **"Spindle"** para parar a rotação da broca.
  <div style="text-align: center;">
    <img src="Imagens/botao-parar.png" alt="botao-parar" style="max-width: 200px;">
  </div>

## 7. ✅ Finalização

* Após a conclusão da fresagem, retire a placa da fresadora.
