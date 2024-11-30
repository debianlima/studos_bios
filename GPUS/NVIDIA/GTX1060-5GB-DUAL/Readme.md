Para identificar o **ID do Dispositivo** (Device ID) da sua GPU no Linux, você pode utilizar o comando `lspci` com opções específicas para exibir os IDs numéricos dos dispositivos. Isso é especialmente útil ao configurar drivers ou solucionar problemas de hardware.

## Passo a Passo:

### 1. Identificar o Endereço PCI da GPU:

Execute o seguinte comando para listar todos os dispositivos PCI relacionados a controladores VGA ou 3D:

```bash
lspci | grep -E "VGA|3D"
```

A saída será semelhante a:

```
08:00.0 VGA compatible controller: NVIDIA Corporation GP106 [GeForce GTX 1060 5GB] (rev a1)
```

Aqui, `08:00.0` é o endereço do barramento PCI da sua GPU.

### 2. Exibir os IDs Numéricos:

Utilize o comando `lspci` com as opções `-n` e `-s` para mostrar os IDs numéricos do dispositivo específico:

```bash
lspci -n -s 08:00.0
```

A saída será algo como:

```
08:00.0 0300: 10de:1c04 (rev a1)
```

Nesta linha, `10de` é o **ID do Fabricante** (Vendor ID) correspondente à NVIDIA, e `1c04` é o **ID do Dispositivo** (Device ID) específico para a GeForce GTX 1060 5GB.

### 3. Obter Informações Detalhadas:

Para mais detalhes sobre o dispositivo, incluindo o ID do subsistema, execute:

```bash
lspci -vnn -s 08:00.0
```

A opção `-vnn` exibe informações detalhadas juntamente com os IDs numéricos. A saída incluirá linhas como:

```
08:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP106 [GeForce GTX 1060 5GB] [10de:1c04] (rev a1) (prog-                if 00 [VGA controller])
        Subsystem: ASUSTeK Computer Inc. GP106 [GeForce GTX 1060 5GB] [1043:8638]

```

Aqui, `[10de:1c04]` confirma os IDs do Fabricante e do Dispositivo, e `Subsystem: ASUSTeK Computer Inc. Device [1043:85f4]` fornece o ID do subsistema, onde `1043` é o ID do Fabricante do subsistema (ASUS) e `85f4` é o ID do Dispositivo do subsistema.

## Observações:

- O **ID do Dispositivo** é uma identificação única que, juntamente com o **ID do Fabricante**, permite identificar especificamente o hardware. Esses IDs são úteis para determinar a compatibilidade de drivers e para diagnósticos de hardware.

- Ferramentas como `lspci` são essenciais para obter informações detalhadas sobre os dispositivos conectados ao barramento PCI do sistema, auxiliando na configuração e solução de problemas.

Seguindo esses passos, você poderá identificar com precisão o ID do Dispositivo da sua GPU no Linux, o que é fundamental para a instalação de drivers adequados e para a resolução de possíveis problemas relacionados ao hardware gráfico. 
