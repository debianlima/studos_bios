# Documento de Procedimentos: Modificações na BIOS da Placa-Mãe Atermiter X99 V1.41 para Mineração

Este guia detalha as alterações realizadas na BIOS utilizando ferramentas específicas, com foco em otimização para mineração e melhorias gerais no desempenho do sistema. A documentação aborda cada configuração alterada, explicando os impactos e a forma de aplicá-las.

---

## Ferramentas Utilizadas
- **S3TurboTool**: Ajustes de tensão, frequência, e turbo boost.  
- **AMIBCP**: Modificações avançadas de configurações da BIOS.  
- **MMTool Aptio**: Remoção de patches de microcode e substituição de módulos.  
- **UEFITool**: Substituição de módulos específicos na BIOS.

---

## Alterações Realizadas e Impactos

### 1. **Remoção do Patch de Microcode 06F2**
   - **Motivo**: Compatibilidade com CPUs específicas e estabilidade em mineração.  
   - **Impacto**: Remove suporte a CPUs não utilizadas para liberar espaço e melhorar estabilidade.

### 2. **Manutenção da Tensão no Cache (Uncore)**
   - **Configuração**: Cache Voltage Offset mantido em `0mV`.  
   - **Motivo**: Evitar instabilidades que ocorrem ao reduzir a tensão do cache em cargas pesadas.  
   - **Impacto**: Garantia de estabilidade em ambientes de alto uso, como mineração.

### 3. **Habilitar Wake On LAN**
   - **Configuração**: Alterado para `Enabled` no AMIBCP.  
   - **Motivo**: Permitir o ligamento remoto da máquina via rede.  
   - **Impacto**: Facilita a reinicialização e o gerenciamento remoto do sistema.

### 4. **Configuração de Ventiladores para Full Mode**
   - **Configuração**: Alterado para `Full Mode` em todas as entradas de controle de ventiladores.  
   - **Motivo**: Garantir refrigeração máxima, reduzindo risco de superaquecimento durante mineração.  
   - **Impacto**: Aumenta o resfriamento ao custo de ruído mais elevado.

### 5. **Habilitar Above 4G Decoding**
   - **Configuração**: Alterado para `Enabled` no AMIBCP.  
   - **Motivo**: Suporte a GPUs e dispositivos PCIe com endereçamento acima de 4 GB.  
   - **Impacto**: Necessário para rigs de mineração que utilizam múltiplas GPUs.

### 6. **Forçar PCI Express Target Link em 2.5 GT/s**
   - **Configuração**: Ajustado para `2.5 GT/s`.  
   - **Motivo**: Estabilizar a comunicação com dispositivos PCIe.  
   - **Impacto**: Reduz problemas de incompatibilidade e falhas de link em rigs de mineração.

### 7. **Desabilitar Hardware Speed e Width no PCI Express**
   - **Configuração**: Alterado para `Disabled`.  
   - **Motivo**: Evitar ajustes automáticos que podem causar instabilidade.  
   - **Impacto**: Garante estabilidade no barramento PCIe.

### 8. **Desabilitar BIOS Guard**
   - **Configuração**: Alterado para `Disabled`.  
   - **Motivo**: Permitir gravações frequentes e customização da BIOS sem restrições de segurança.  
   - **Impacto**: Facilita modificações, mas aumenta riscos de segurança.

### 9. **Gerenciamento de Energia (C-State Configurações)**
   - **C-State**:  
      - **C1E**: Habilitado.  
      - **C2**: Ajustado para `Enabled`.  
      - **C3**: Ajustado para `Enabled`.  
      - **C6**: Ajustado para `Disabled`.  
   - **Motivo**: Melhorar estabilidade e consumo energético para cargas constantes.  
   - **Impacto**: Reduz consumo desnecessário e otimiza para cargas estáveis.

### 10. **Substituição do Módulo 271C62F2**
   - **Configuração**: Substituído pelo módulo personalizado **Turbo Hack**.  
   - **Motivo**: Ativar melhorias de energia específicas e configurações avançadas de turbo boost.  
   - **Impacto**: Garantia de melhor desempenho sob cargas constantes.

---

## Passo a Passo para Aplicar as Alterações

### Passo 1: Backup da BIOS Atual
Utilize o comando abaixo para fazer o backup:
```bash
sudo flashrom -p internal -r backup_bios.bin
```

### Passo 2: Remover o Patch 06F2 com MMTool
1. Abra a BIOS no **MMTool**.  
2. Navegue até a aba **CPU Patch** e remova o patch `06F2`.

### Passo 3: Substituir o Módulo 271C62F2 no UEFITool
1. Carregue a BIOS no **UEFITool**.  
2. Localize o módulo `271C62F2` e substitua pelo módulo personalizado **Turbo Hack**.  
3. Salve a BIOS modificada.

### Passo 4: Alterações no AMIBCP
1. Carregue a BIOS no **AMIBCP**.  
2. Faça as seguintes alterações:
   - **Power On After Power Loss**: Alterar para `On`.  
   - **Wake On LAN**: Alterar para `Enabled`.  
   - **Fan Control**: Ajustar todos os ventiladores para `Full Mode`.  
   - **Above 4G Decoding**: Alterar para `Enabled`.  
   - **PCI Express Target Link**: Ajustar para `2.5 GT/s`.  
   - **Hardware Speed e Width PCI Express**: Alterar para `Disabled`.  
   - **C-States**: Configure C1E, C2 e C3 como `Enabled` e C6 como `Disabled`.  

### Passo 5: Aplicar as Configurações no S3TurboTool
1. Configure as tensões:
   - **Core Voltage Offset**: `-20mV`.  
   - **Agent Voltage Offset**: `-20mV`.  
   - **Cache Voltage Offset**: `0mV`.  
2. Habilite o **Turbo Unlock (20x20)**.

### Passo 6: Gravar a BIOS Modificada
Utilize o comando abaixo para gravar a BIOS:
```bash
sudo flashrom -p internal -w bios_modificada.bin
```

---

## Impacto Resumido

| Alteração                      | Impacto em Mineração                  | Impacto em Uso Geral                  |
|--------------------------------|---------------------------------------|---------------------------------------|
| **Turbo Unlock**               | Aumenta hashrate                     | Melhora o desempenho multitarefa      |
| **Cache Tensão Mantida**       | Garante estabilidade                 | Evita travamentos                     |
| **Wake On LAN**                | Permite controle remoto              | Útil para gerenciamento               |
| **Fan em Full Mode**           | Resfria GPUs e CPUs                  | Eleva ruído do sistema                |
| **Above 4G Decoding**          | Suporte a múltiplas GPUs             | Necessário para rigs avançados        |
| **PCIe Target Link 2.5 GT/s**  | Estabiliza comunicação               | Reduz problemas com dispositivos PCIe |
| **C-States Configurados**      | Reduz consumo energético             | Menor impacto em tarefas esporádicas  |

---

## Observações Finais

Para mais informações e suporte técnico, consulte a documentação e arquivos do repositório:
- [Placa-Mãe Atermiter X99 V1.41](https://github.com/debianlima/studos_bios/tree/main/motherboards/Atermiter/x99_v1.41)
- [Readme Unlook Miner](https://github.com/debianlima/studos_bios/blob/main/motherboards/Atermiter/x99_v1.41/readmeunlookminer.md) 

As modificações descritas foram testadas com sucesso em ambientes de mineração e desktops, garantindo estabilidade e desempenho aprimorados.
