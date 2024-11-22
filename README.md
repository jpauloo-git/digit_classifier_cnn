# digit_classifier_cnn

Esse código define um sistema para classificar dígitos de 0 a 9 em uma imagem 8x8, usando redes neurais convolucionais (CNN). A seguir, umabreve explicação para as pricipais cada partes do código.

Importação de bibliotecas:

numpy, matplotlib.pyplot, random para manipulação de dados e visualização.
tensorflow.keras para definir e treinar o modelo de rede neural.
Definição dos padrões de dígitos:

Um dicionário digit_patterns é criado, onde cada chave representa um dígito (0 a 9) e cada valor é uma matriz 8x8 de zeros e uns, representando uma versão binária do dígito.
Função add_binary_noise:

Essa função adiciona ruído aleatório a uma imagem binária.
noise_level define a proporção de pixels que serão alterados. Cada pixel selecionado é invertido (de 1 para 0 ou de 0 para 1).
Ela permite gerar variações ruidosas dos dígitos, o que ajuda a tornar o modelo mais robusto.
Geração dos dados de treinamento:

Para cada dígito, várias versões ruidosas são criadas (10.000 variações por dígito) e armazenadas em X_train.
y_train armazena as respectivas classes (0 a 9).
Após a criação dos dados, X_train é convertido para um array numpy com dimensão (N, 8, 8, 1), necessário para o modelo convolucional. y_train é convertido para one-hot encoding usando to_categorical, criando uma matriz com 10 colunas (uma para cada dígito).
Divisão dos dados de treinamento e validação:

train_test_split divide X_train e y_train em conjuntos de treinamento e validação, usando 25% dos dados para validação.
Definição do modelo:

O modelo definido é uma rede neural convolucional que combina:
Conv2D: Camada convolucional com 16 filtros 3x3 para extrair características das imagens.
MaxPooling2D: Camada de pooling para reduzir a dimensionalidade.
Dropout: Camadas de dropout (25% e 50%) para prevenir overfitting.
Flatten: Converte os dados para uma dimensão, permitindo a conexão com camadas densas.
Dense: Camadas densas para a classificação, incluindo a última camada com 10 neurônios e ativação softmax para gerar a probabilidade de cada classe.
Esse modelo convolucional permite ao sistema identificar o dígito nas imagens de 8x8, mesmo com variações de ruído.
