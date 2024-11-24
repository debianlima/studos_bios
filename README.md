
# Estudos de BIOS

Este repositório é dedicado ao estudo, gravação e modificação de BIOS, com o objetivo de compartilhar experiências e conhecimentos relacionados à eletrônica envolvida, além de indicar softwares e procedimentos práticos. Abaixo estão alguns dos principais tópicos abordados:

## Principais Tópicos

- **Experiências de Gravação:** Relatos e resultados de diferentes métodos e ferramentas para gravação de BIOS, incluindo desafios enfrentados e soluções encontradas.
- **Modificação de BIOS:** Análise e customização de BIOS para uso avançado, discutindo modificações permitidas e limites de segurança.
- **Entendimento da Eletrônica de BIOS:** Explicação dos componentes eletrônicos e do funcionamento dos chips de BIOS, desde esquemáticos até identificação de falhas.
- **Softwares e Procedimentos:** Recomendação de ferramentas e passos para gravação, leitura e modificação de BIOS, com tutoriais e boas práticas para iniciantes e experientes.

Este repositório é destinado a técnicos, entusiastas e desenvolvedores que desejam aprimorar seus conhecimentos em gravação e modificação de BIOS, bem como entender melhor a eletrônica que envolve esses chips essenciais.

---

## Configuração de Pinos do Chip de BIOS

| Pino | Função       | Descrição                                                                                    | Tensão                       |
|------|--------------|---------------------------------------------------------------------------------------------|------------------------------|
| 1    | /CS          | Chip Select – Ativa o chip para comunicação; ativo em 0 V e inativo em 1,8 V               | 1,8 V (inativo) / 0 V (ativo) |
| 2    | DO (Data Out) | Dados de saída do chip para o controlador                                                  | Alterna entre 0 e 1,8 V      |
| 3    | WP (Write Protect) | Proteção de gravação; ativo em 0 V para proteger contra gravação, inativo em 1,8 V     | 0 V (ativado) / 1,8 V (desativado) |
| 4    | GND          | Terra                                                                                       | 0 V                          |
| 5    | DI (Data In) | Dados de entrada do controlador para o chip                                                | Alterna entre 0 e 1,8 V      |
| 6    | CLK (Clock)  | Sinal de clock fornecido pelo controlador                                                  | Alterna entre 0 e 1,8 V      |
| 7    | HOLD (ou Reset) | Coloca o chip em estado de espera ou reset quando mantido em 0 V, funcionando normalmente em 1,8 V | 0 V (espera) / 1,8 V (operacional) |
| 8    | VCC          | Alimentação do chip                                                                         | 1,8 V                        |

Esta tabela reflete a configuração de pinos conforme o datasheet, incluindo as tensões típicas e o funcionamento de cada pino para operação com um chip de 1,8 V da série 25.

---

## Orientações para Gravação de BIOS

Gravar uma BIOS requer atenção ao modelo do chip e ao uso correto de ferramentas e softwares. Abaixo estão os passos gerais para realizar a gravação de uma BIOS:

### Passos Gerais

1. **Identifique o chip de BIOS:** Use ferramentas como `flashrom` ou examine fisicamente a placa para encontrar o modelo do chip.
2. **Faça um backup do firmware atual:** Antes de gravar, leia e salve o firmware atual com o comando:
   ```sh
   sudo flashrom -p internal -r backup_bios.bin
   ```
   Isso criará um arquivo chamado `backup_bios.bin` com o conteúdo da BIOS.
3. **Prepare o novo firmware:** Verifique se o arquivo da nova BIOS é compatível com seu chip e placa-mãe.
4. **Grave o firmware:** Para gravar o novo firmware, use:
   ```sh
   sudo flashrom -p internal -w novo_firmware.bin
   ```
   Substitua `novo_firmware.bin` pelo nome do arquivo que contém o firmware que você deseja gravar.
5. **Verifique a gravação:** Após gravar, valide a operação com:
   ```sh
   sudo flashrom -p internal -v novo_firmware.bin
   ```
   Isso verifica se o firmware foi gravado corretamente.

### Ferramentas Recomendadas

- **Flashrom:** Utilitário open-source para gravação e leitura de chips de BIOS.
- **CH341A:** Programador externo para gravação em chips desconectados da placa-mãe.
- **Hex Editor:** Ferramenta para análise e modificação do firmware em nível binário.

Consulte a documentação do fabricante e teste cuidadosamente para evitar danos ao firmware do sistema.

---

## Informações sobre a Placa-Mãe Atermiter X99 V1.41

A placa-mãe abordada neste repositório é o modelo **Atermiter X99 V1.41**, projetada para processadores Intel Xeon e com suporte ao chipset Intel 8 Series/C220. Abaixo estão os detalhes da placa:

| Especificação       | Detalhes                        |
|---------------------|----------------------------------|
| Fabricante          | Atermiter                       |
| Modelo              | X99 V1.41                       |
| Chipset             | Intel 8 Series/C220             |
| BIOS Modificada     | [Link para BIOS](https://github.com/debianlima/studos_bios/blob/main/motherboards/Atermiter/x99_v1.41/bios_x99_powerlost_20x20_turbo_hack.bin) |
|Unlock para Minerar  | [Alterações Explicadas](https://github.com/debianlima/studos_bios/blob/main/motherboards/Atermiter/x99_v1.41/readmeunlookminer.md) |


---

## Identificar e Obter a BIOS da Placa-Mãe

Para obter informações detalhadas sobre como identificar e gravar a BIOS, consulte a seção [Como Identificar Informações da Placa-Mãe no Linux](https://github.com/debianlima/studos_bios/blob/main/motherboards/Atermiter/readme.md).

---
```
