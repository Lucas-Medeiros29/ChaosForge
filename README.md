# ChaosForge
ChaosForge é um framework open-source para descoberta automática, evolução e classificação de atratores caóticos via experimentação computacional massiva.O objetivo é construir um catálogo sistemático de dinâmicas não lineares, com métricas rigorosas e mecanismos de detecção de novidade estrutural, possívelmente um passo em direção a uma futura taxonomia universal de atratores estranhos.

# Motivação

Atratores estranhos são estruturas geométricas que emergem de sistemas dinâmicos dissipativos não lineares. Exemplos clássicos incluem os sistemas de:

- Edward Lorenz
- Otto Rössler
- Michel Hénon

Apesar da importância histórica, a exploração do espaço de sistemas dinâmicos permanece amplamente artesanal.

ChaosForge propõe:

- Exploração automatizada do espaço paramétrico

- Evolução computacional de dinâmicas

- Avaliação quantitativa rigorosa de caos

- Detecção automática de novidade estrutural

- Construção progressiva de um atlas de atratores

# Objetivos do Projeto:

- Gerar automaticamente sistemas dinâmicos contínuos ou discretos

- Avaliar caos via métricas numéricas robustas

- Evoluir sistemas com algoritmos evolucionários

- Detectar estruturas dinâmicas inéditas

- Classificar atratores por invariantes aproximados

- Construir um dataset aberto para pesquisa futura

# Arquitetura
chaosforge/
│
├── core/           # Definição de sistemas dinâmicos
├── integrators/    # Métodos numéricos (RK4, RK45)
├── metrics/        # Lyapunov, dimensão fractal, entropia
├── evolution/      # Algoritmos genéticos / CMA-ES
├── novelty/        # Métricas de distância estrutural
├── topology/       # Invariantes e testes de conjugação
├── visualization/  # Plotagens e seções de Poincaré
├── experiments/    # Configurações replicáveis
└── cli.py


A separação modular permitir extensões futuras.

# Tipos de Sistemas Suportados (v1):
1. Sistemas polinomiais 3D (grau ≤ 2) com termos até grau 2.

2. Mapas discretos 2D e 3D

3. Extensões futuras:

- Sistemas híbridos
- Redes neurais mínimas
- Dinâmica simbólica

# Métricas Implementadas

Cada sistema candidato é avaliado por:
- Expoente máximo de Lyapunov
- Dimensão de Kaplan–Yorke
- Divergência média (dissipatividade)
- Teste de explosão numérica
- Entropia aproximada

Critério mínimo de caos:
- λ_max > 0
- Trajetória limitada
- Não convergência periódica

# Detecção de Novidade

Para evitar redescobrir variações triviais de sistemas conhecidos:

- Distância entre espectros de Lyapunov
- Distância Wasserstein entre distribuições no espaço de estados
- Comparação de histogramas de retorno
- Clustering não supervisionado

Fitness multiobjetivo:
- Maximizar caos
- Maximizar distância estrutural

# Exemplo de Uso
python cli.py --config experiments/default.yaml


Saída gerada automaticamente:

results/
 ├── attractor_001/
 │    ├── metrics.json
 │    ├── trajectory.npy
 │    ├── lyapunov.txt
 │    └── plot.png

# Experimento Reprodutível Inicial

Configuração padrão:
- 200 indivíduos
- 100 gerações
- Integração RK4
- 5000 passos por simulação
- Seleção elitista 20%

Todos os experimentos devem ser totalmente reprodutíveis via seed fixa.

# Roadmap
# v0.1

- Evolução básica de sistemas polinomiais
- Cálculo confiável de Lyapunov

# v0.2

- Detecção automática de novidade
- Banco de dados interno de atratores

# v0.3

- Classificação topológica aproximada
- Exportação de dataset estruturado

# v1.0

- Atlas público de atratores
- Paper submetido

# Potenciais Impactos

- Exploração sistemática do espaço de dinâmicas não lineares
- Dataset para aprendizado de representações dinâmicas
- Base para computação baseada em caos
- Possível estrutura emergente para taxonomia universal

# Requisitos

- Python 3.10+
- NumPy
- SciPy
- Matplotlib
- scikit-learn
- (futuro) JAX ou PyTorch

# Contribuições

Contribuições são bem-vindas nas áreas de:

- Métodos numéricos mais estáveis
- Estimadores robustos de invariantes
- Técnicas de homologia persistente
- Otimização evolutiva avançada

# Licença

MIT License

# Visão de Longo Prazo

Se o espaço de atratores possui estrutura profunda, ela emergirá apenas por exploração sistemática, classificação rigorosa e análise estatística em larga escala.

ChaosForge é um primeiro passo nessa direção.
