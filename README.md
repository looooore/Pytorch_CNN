# Classificação de Dígitos MNIST com Redes Neurais Convolucionais (CNN)

Este projeto apresenta a implementação de uma **Rede Neural Convolucional (CNN)** utilizando a biblioteca **PyTorch** para a classificação de dígitos manuscritos do conjunto de dados **MNIST**. O objetivo principal é demonstrar o fluxo completo de um projeto de Deep Learning, desde o carregamento e transformação dos dados até o treinamento e avaliação do modelo.

> **Nota:** Este projeto foi desenvolvido com fins de estudo e aprendizado pessoal sobre a aplicação de Redes Neurais Convolucionais e o framework PyTorch.

O notebook faz parte do repositório [Pytorch_Colab](https://github.com/looooore/Pytorch_Colab) e foi desenvolvido para ser executado em ambientes como o Google Colab, aproveitando a facilidade de visualização e integração com ferramentas de ciência de dados.

## O que é uma Rede Neural Convolucional (CNN)?

Uma **Rede Neural Convolucional (CNN)**, ou ConvNet, é uma classe de redes neurais profundas mais comumente aplicada à análise de imagens visuais. Seu nome deriva da operação matemática de **convolução**, que é o principal bloco de construção da arquitetura.

As CNNs são projetadas para processar dados de pixel com uma topologia de array conhecida, como imagens 2D. Elas usam camadas de convolução para aprender automaticamente e espacialmente hierarquias de recursos a partir dos dados de entrada. Isso significa que a rede pode aprender a reconhecer padrões simples (como bordas e texturas) nas primeiras camadas e, gradualmente, padrões mais complexos (como formas e objetos) nas camadas mais profundas.

## O Dataset MNIST

O **MNIST** (Modified National Institute of Standards and Technology) é um dos conjuntos de dados mais clássicos e amplamente utilizados no campo de Machine Learning e Deep Learning. Ele consiste em uma coleção de **70.000 imagens em escala de cinza de dígitos manuscritos** (0 a 9), sendo 60.000 para treinamento e 10.000 para teste.

Cada imagem no dataset MNIST tem um tamanho de **28x28 pixels**. O objetivo principal ao usar este dataset é treinar um modelo para classificar corretamente cada imagem no dígito correspondente. Por sua simplicidade e clareza, o MNIST é frequentemente usado como o "Hello World" do Deep Learning para testar novas arquiteturas e técnicas.

## Estrutura do Modelo

A arquitetura da rede foi projetada seguindo o padrão clássico de redes convolucionais, alternando camadas de convolução, ativação e pooling antes de passar para as camadas densas (totalmente conectadas).

| Camada | Tipo | Configuração |
| :--- | :--- | :--- |
| **Conv1** | Convolucional | 1 canal de entrada, 6 filtros, kernel 3x3, stride 1 |
| **Pool1** | Max Pooling | Kernel 2x2, stride 2 |
| **Conv2** | Convolucional | 6 canais de entrada, 16 filtros, kernel 3x3, stride 1 |
| **Pool2** | Max Pooling | Kernel 2x2, stride 2 |
| **FC1** | Linear | Entrada de 400 (5x5x16) para 120 neurônios |
| **FC2** | Linear | 120 para 84 neurônios |
| **FC3** | Linear | 84 para 10 classes (saída final) |

A função de ativação utilizada entre as camadas é a **ReLU** (Rectified Linear Unit), e a saída final utiliza a função **Log Softmax** para a classificação das 10 categorias de dígitos (0 a 9).

## Tecnologias e Bibliotecas

O projeto utiliza as principais bibliotecas do ecossistema Python para Inteligência Artificial e análise de dados:

*   **PyTorch**: Framework principal para construção e treinamento da rede neural.
*   **Torchvision**: Utilizada para carregar o dataset MNIST e aplicar transformações nas imagens.
*   **Matplotlib**: Para visualização das imagens do dataset e plotagem dos gráficos de desempenho (perda e acurácia).
*   **NumPy & Pandas**: Para manipulação eficiente de dados e matrizes.
*   **Scikit-Learn**: Utilizada especificamente para a geração da matriz de confusão, permitindo uma análise detalhada dos erros do modelo.

## Configurações de Treinamento

O treinamento foi configurado para otimizar a precisão do modelo de forma eficiente:

> **Dataset:** MNIST (60.000 imagens de treino, 10.000 de teste)
> **Otimizador:** Adam com taxa de aprendizado (learning rate) de 0.001
> **Função de Perda:** Cross Entropy Loss
> **Tamanho do Lote (Batch Size):** 10

## Como Utilizar

Para executar este projeto localmente ou no Google Colab, siga os passos abaixo:

1.  Clone o repositório:
    ```bash
    git clone https://github.com/looooore/Pytorch_Colab.git
    ```
2.  Instale as dependências necessárias:
    ```bash
    pip install torch torchvision matplotlib numpy pandas scikit-learn
    ```
3.  Abra o arquivo `CNN.ipynb` em seu ambiente Jupyter ou Colab e execute as células sequencialmente.

O código fará o download automático do dataset MNIST na primeira execução e iniciará o processo de treinamento, exibindo o progresso de perda a cada intervalo de lotes.
