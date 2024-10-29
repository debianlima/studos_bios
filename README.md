

<h1>Estudos de BIOS</h1>

<p>Este repositório é dedicado ao estudo, gravação e modificação de BIOS, com o objetivo de compartilhar experiências e conhecimentos relacionados à eletrônica envolvida, além de indicar softwares e procedimentos práticos. Abaixo estão alguns dos principais tópicos abordados:</p>

<h2>Principais Tópicos</h2>
<ul>
    <li><strong>Experiências de Gravação:</strong> Relatos e resultados de diferentes métodos e ferramentas para gravação de BIOS, incluindo desafios enfrentados e soluções encontradas.</li>
    <li><strong>Modificação de BIOS:</strong> Análise e customização de BIOS para uso avançado, discutindo modificações permitidas e limites de segurança.</li>
    <li><strong>Entendimento da Eletrônica de BIOS:</strong> Explicação dos componentes eletrônicos e do funcionamento dos chips de BIOS, desde esquemáticos até identificação de falhas.</li>
    <li><strong>Softwares e Procedimentos:</strong> Recomendação de ferramentas e passos para gravação, leitura e modificação de BIOS, com tutoriais e boas práticas para iniciantes e experientes.</li>
</ul>

<p>Este repositório é destinado a técnicos, entusiastas e desenvolvedores que desejam aprimorar seus conhecimentos em gravação e modificação de BIOS, bem como entender melhor a eletrônica que envolve esses chips essenciais.</p>

<h2>Configuração de Pinos do Chip de BIOS</h2>

<table>
    <thead>
        <tr>
            <th>Pino</th>
            <th>Função</th>
            <th>Descrição</th>
            <th>Tensão</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>1</td>
            <td>/CS</td>
            <td>Chip Select – Ativa o chip para comunicação; ativo em 0 V e inativo em 1,8 V</td>
            <td>1,8 V (inativo) / 0 V (ativo)</td>
        </tr>
        <tr>
            <td>2</td>
            <td>DO (Data Out)</td>
            <td>Dados de saída do chip para o controlador</td>
            <td>Alterna entre 0 e 1,8 V</td>
        </tr>
        <tr>
            <td>3</td>
            <td>WP (Write Protect)</td>
            <td>Proteção de gravação; ativo em 0 V para proteger contra gravação, inativo em 1,8 V</td>
            <td>0 V (ativado) / 1,8 V (desativado)</td>
        </tr>
        <tr>
            <td>4</td>
            <td>GND</td>
            <td>Terra</td>
            <td>0 V</td>
        </tr>
        <tr>
            <td>5</td>
            <td>DI (Data In)</td>
            <td>Dados de entrada do controlador para o chip</td>
            <td>Alterna entre 0 e 1,8 V</td>
        </tr>
        <tr>
            <td>6</td>
            <td>CLK (Clock)</td>
            <td>Sinal de clock fornecido pelo controlador</td>
            <td>Alterna entre 0 e 1,8 V</td>
        </tr>
        <tr>
            <td>7</td>
            <td>HOLD (ou Reset)</td>
            <td>Coloca o chip em estado de espera ou reset quando mantido em 0 V, funcionando normalmente em 1,8 V</td>
            <td>0 V (espera) / 1,8 V (operacional)</td>
        </tr>
        <tr>
            <td>8</td>
            <td>VCC</td>
            <td>Alimentação do chip</td>
            <td>1,8 V</td>
        </tr>
    </tbody>
</table>

<p>Esta tabela reflete a configuração de pinos conforme o data sheet, incluindo as tensões típicas e o funcionamento de cada pino para operação com um chip de 1,8 V da série 25.</p>


