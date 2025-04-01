# 🚀 Análise dos Protocolos de Teletransporte Quântico e BB84 🛰 

Bem-vindo(a) ao repositório de **Simulações de Teletransporte Quântico e Distribuição de Chaves Quânticas (BB84)** utilizando canais satélite-terra. Este projeto integra a framework [NetSquid](https://netsquid.org) para redes quânticas com [Skyfield](https://rhodesmill.org/skyfield/) para cálculos de trajetórias de satélites, trazendo um toque futurista e de ficção científica para a pesquisa em comunicações quânticas.

---

## 🌌 Visão Geral

Este repositório apresenta simulações que englobam:

- **Teletransporte Quântico**
  - Modelos para perda de fótons em espaço livre e canais satélite-terra (*FreeSpaceLossModel*, *FixedSatelliteLossModel*).
  - Análise de trajetórias de satélites utilizando dados TLE (Two-Line Element).
  - Estudos de fidelidade em diferentes condições de canal e taxas de despolarização.
  - Visualizações dinâmicas do estado quântico (matrizes de densidade, funções de Wigner).

- **Protocolo BB84 de QKD**
  - Simulação do protocolo BB84 em links satélite-terra.
  - Análise de taxa de chave para diferentes satélites (por exemplo, Starlink, Iridium, Amazonia-1).
  - Integração com passagens reais de satélites e estações terrestres (Campinas, Belém).

- **Ferramentas de Satélite**
  - Cálculos de distância e ângulo de elevação durante as passagens dos satélites.
  - Comparação de desempenho dos canais quânticos entre diversos satélites.

---

## 🔧 Instalação

### Dependências
- **Python 3.8+**

### Pacotes Necessários
Utilize o `pip` para instalar as dependências:
```bash
pip install --extra-index-url https://pypi.netsquid.org netsquid skyfield numpy matplotlib scipy pandas seaborn qutip pycryptodome
```

## 🛠️ Uso
Teletransporte Quântico (TelePorts.ipynb)

Definir Parâmetros do Satélite:

```bash
tle_IRIDIUM_122 = """
1 42957U 17061C   25007.49702594  .00000117  00000+0  34556-4 0  9991
2 42957  86.3957 244.8288 0001777  86.7983 273.3416 14.34214161379435
"""
```

Simular Perda no Canal:

```bash
model = FixedSatelliteLossModel(txDiv=1e-6, sigmaPoint=0.5e-8, ...)
Executar a Simulação de Teletransporte:
```

```bash
network = example_network_setup(node_distance=800, depolar_rate=1e1)
ns.sim_run()
```


### Protocolo BB84 (SatBB84.ipynb)
Configurar a Estação Terrestre:

```bash
down_channel = DownChannel(tle_IRIDIUM_122, lat=-22.8542, lon=-47.0220, alt=0)
```
Executar a Simulação do Protocolo BB84:
```bash
protocol = BB84(num_bits=200, fibre_len=1500)
key_list = run_BB84_sim(runtimes=10, num_bits=200)
```

## 📚 Referências
NetSquid: netsquid.org

Skyfield: rhodesmill.org/skyfield/

Referência Científica: Vasylyev et al., PRL 108, 220501 (2012) – Modelo de perda em espaço livre.

Nota: Atualize os dados TLE no código para trajetórias atuais dos satélites. As simulações consideram condições idealizadas; ajuste parâmetros atmosféricos (Cn²) e de hardware (por exemplo, diâmetro do telescópio) para outros cenários.
