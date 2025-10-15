# Living IA - Plataforma de Análise Imobiliária com Inteligência Artificial

## 📋 Sobre o Projeto

Living IA é uma plataforma completa de análise imobiliária que utiliza Inteligência Artificial e Machine Learning para fornecer insights avançados sobre o mercado imobiliário. O sistema permite análise de imóveis (apartamentos e lotes) em diferentes cidades, oferecendo clustering inteligente, previsão de preços e visualizações interativas através de dashboards dinâmicos.

## ✨ Principais Funcionalidades

### Autenticação e Gerenciamento de Usuários
- Sistema completo de registro e login de usuários
- Autenticação segura com validação de credenciais
- Gerenciamento de sessões de usuário

### Análise Inteligente de Dados Imobiliários
- **Clustering com K-means**: Agrupamento automático de imóveis por características
- **Previsão de Preços**: Modelo Random Forest para predição de valores
- **Remoção de Outliers**: Tratamento automático de dados usando método IQR
- **Análise por Cidade**: Insights específicos para Campinas, Americana e Paulínia

### Dashboard Interativo
- Visualizações dinâmicas com gráficos interativos
- Análise de preço por área
- Distribuição de preços e áreas
- Estatísticas por cluster (alto/baixo preço)
- Cards com métricas resumidas (preço médio, área média, total de imóveis)

### API RESTful
- Endpoints para gerenciamento de dados de apartamentos e lotes
- Integração com MongoDB para persistência de dados
- CORS habilitado para comunicação frontend/backend

## 🛠️ Tecnologias Utilizadas

### Backend
- **Python 3.x**
- **Flask**: Framework web para API REST
- **Flask-CORS**: Gerenciamento de CORS
- **Pandas**: Manipulação e análise de dados
- **Plotly**: Visualizações de dados
- **Dash**: Framework para dashboards interativos
- **Scikit-learn**: Machine Learning
  - K-means Clustering
  - Random Forest Regressor
  - StandardScaler
- **PyMongo**: Integração com MongoDB
- **NumPy**: Operações numéricas

### Frontend
- **Vue 3**: Framework JavaScript progressivo
- **TypeScript**: Superset tipado do JavaScript
- **Vite**: Build tool e dev server
- **Vue Router**: Gerenciamento de rotas
- **Pinia**: Gerenciamento de estado
- **Axios**: Cliente HTTP para requisições
- **Tailwind CSS**: Framework de estilização
- **PostCSS**: Processamento de CSS

### Banco de Dados
- **MongoDB Atlas**: Banco de dados NoSQL em nuvem

## 📦 Pré-requisitos

- **Python**: 3.8 ou superior
- **Node.js**: 16.x ou superior
- **npm**: 8.x ou superior
- **MongoDB Atlas**: Conta e cluster configurado (ou MongoDB local)
- **Git**: Para controle de versão

## 🚀 Instalação e Configuração

### 1. Clone o Repositório

```bash
git clone https://github.com/JONTK123/PI5-LivingIA.git
cd PI5-LivingIA
```

### 2. Configuração do Backend

#### Instalar Dependências Python

```bash
# Criar ambiente virtual (recomendado)
python -m venv venv

# Ativar ambiente virtual
# No Windows:
venv\Scripts\activate
# No Linux/Mac:
source venv/bin/activate

# Instalar dependências
pip install -r requirements.txt
```

#### Dependências Python Necessárias

As principais bibliotecas que serão instaladas:
- Flask
- Flask-CORS
- pandas
- plotly
- dash
- scikit-learn
- pymongo
- numpy

#### Configurar Variáveis de Ambiente

Crie um arquivo `.env` na raiz do projeto (caso não exista) e configure:

```env
MONGODB_URI=sua_connection_string_mongodb
DATABASE_NAME=living_datas
```

**Nota**: Por segurança, atualize a string de conexão no arquivo `backend/handlers/mongo_handler.py` com suas próprias credenciais.

### 3. Configuração do Frontend

```bash
cd frontend/well-living

# Instalar dependências
npm install

# Ou usar yarn
yarn install
```

## 🎮 Executando a Aplicação

### Iniciar o Backend

```bash
# Na raiz do projeto
python -m backend.api.app

# Ou
cd backend/api
python app.py
```

O servidor Flask será iniciado em: `http://localhost:5000`

#### Endpoints Disponíveis

**Dados e Teste:**
- `GET /data` - Dados de exemplo
- `GET /mongo` - Testar conexão MongoDB

**Lotes:**
- `GET /mongo/get/lotes` - Buscar todos os lotes
- `POST /mongo/insert/lotes` - Inserir um lote
- `POST /mongo/insert_all/lotes` - Inserir múltiplos lotes

**Apartamentos:**
- `GET /mongo/get/apartamentos` - Buscar todos os apartamentos
- `POST /mongo/insert/apartamentos` - Inserir um apartamento
- `POST /mongo/insert_all/apartamentos` - Inserir múltiplos apartamentos

**Autenticação:**
- `POST /auth/login` - Login de usuário
  ```json
  {
    "email": "usuario@email.com",
    "password": "senha"
  }
  ```
- `POST /auth/register` - Registro de novo usuário
  ```json
  {
    "name": "Nome do Usuário",
    "email": "usuario@email.com",
    "password": "senha"
  }
  ```

**Dashboard:**
- `GET /dash/` - Dashboard interativo com análises de IA

### Iniciar o Frontend

```bash
cd frontend/well-living

# Modo desenvolvimento
npm run dev

# Build para produção
npm run build

# Preview do build de produção
npm run preview
```

O servidor de desenvolvimento será iniciado em: `http://localhost:5173`

## 📁 Estrutura do Projeto

```
PI5-LivingIA/
├── backend/
│   ├── api/
│   │   ├── __init__.py
│   │   └── app.py              # Aplicação Flask principal
│   ├── handlers/
│   │   ├── __init__.py
│   │   └── mongo_handler.py    # Handler MongoDB
│   ├── models/
│   │   ├── __init__.py
│   │   └── document.py         # Modelo de documento
│   ├── __init__.py
│   ├── dashboard.py            # Dashboard Dash/Plotly
│   ├── ia_analysis.py          # Algoritmos de ML/IA
│   └── documents_list.py       # Lista de documentos de exemplo
├── frontend/
│   └── well-living/
│       ├── public/             # Arquivos públicos estáticos
│       ├── src/
│       │   ├── assets/         # Assets (imagens, estilos, etc)
│       │   ├── components/     # Componentes Vue reutilizáveis
│       │   ├── composables/    # Composables Vue (useAuth)
│       │   ├── router/         # Configuração de rotas
│       │   ├── services/       # Serviços (auth.ts, etc)
│       │   ├── views/          # Views/Páginas
│       │   │   ├── Dashboard.vue
│       │   │   ├── Login.vue
│       │   │   └── Register.vue
│       │   ├── App.vue         # Componente raiz
│       │   └── main.ts         # Entry point
│       ├── index.html
│       ├── package.json
│       ├── vite.config.ts      # Configuração Vite
│       ├── tsconfig.json       # Configuração TypeScript
│       └── tailwind.config.js  # Configuração Tailwind
├── .env                        # Variáveis de ambiente
├── .gitignore
├── requirements.txt            # Dependências Python
└── README.md                   # Este arquivo
```

## 🤖 Algoritmos de Machine Learning

### Clustering K-means
O sistema utiliza K-means para agrupar imóveis em clusters baseados em:
- Área em metros quadrados
- Preço por metro quadrado

Os dados são normalizados usando `StandardScaler` antes do clustering para garantir que ambas as features tenham peso igual.

### Previsão de Preços com Random Forest
Um modelo Random Forest Regressor é treinado para prever preços por metro quadrado baseado em:
- Área do imóvel
- Características do cluster

O modelo é avaliado usando:
- **MSE** (Mean Squared Error)
- **R²** (Coeficiente de Determinação)

### Tratamento de Outliers
Método IQR (Interquartile Range) é aplicado para remover outliers antes da análise:
- Q1: Primeiro quartil (25%)
- Q3: Terceiro quartil (75%)
- IQR = Q3 - Q1
- Limites: [Q1 - 1.5×IQR, Q3 + 1.5×IQR]

## 🎨 Páginas da Aplicação

### Login (`/login`)
- Página de autenticação de usuários existentes
- Validação de email e senha
- Redirecionamento para dashboard após login bem-sucedido

### Registro (`/register`)
- Cadastro de novos usuários
- Validação de dados
- Verificação de email duplicado

### Dashboard (`/dashboard`)
- Interface principal da aplicação
- Seleção de tipo de imóvel (Apartamentos/Lotes)
- Seleção de cidade (Campinas/Americana/Paulínia)
- Visualizações interativas
- Métricas e estatísticas em tempo real

## 🗄️ Coleções do MongoDB

### `usuarios`
```json
{
  "name": "string",
  "email": "string",
  "password": "string"
}
```

### `apartamentos` e `lotes`
```json
{
  "valor": "string",
  "localizacao": "string",
  "tipologia": "string",
  "area_m_quadrados": "string",
  "preco_m": "string",
  "cidade": "string",
  "cluster": "number"
}
```

## 🔒 Segurança

- **Senhas**: Atualmente armazenadas em texto plano (⚠️ Recomenda-se implementar hash de senhas com bcrypt)
- **CORS**: Configurado para permitir requisições cross-origin
- **Validação**: Validação de entrada em todos os endpoints de API
- **MongoDB**: Credenciais devem ser armazenadas em variáveis de ambiente

## 🧪 Testando a Aplicação

### Testar Conexão com MongoDB

```bash
curl http://localhost:5000/mongo
```

### Testar Login

```bash
curl -X POST http://localhost:5000/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"test@email.com","password":"senha123"}'
```

### Testar Inserção de Dados

```bash
curl -X POST http://localhost:5000/mongo/insert/lotes
```

## 🚧 Melhorias Futuras

- [ ] Implementar hash de senhas (bcrypt/argon2)
- [ ] Adicionar autenticação JWT
- [ ] Implementar testes unitários e de integração
- [ ] Adicionar validação de formulários no frontend
- [ ] Implementar paginação nas listagens
- [ ] Adicionar filtros avançados de busca
- [ ] Criar documentação interativa da API (Swagger/OpenAPI)
- [ ] Implementar cache de dados frequentes
- [ ] Adicionar mais modelos de ML (regressão linear, gradient boosting)
- [ ] Implementar upload de arquivos CSV para importação de dados
- [ ] Adicionar exportação de relatórios em PDF
- [ ] Implementar notificações em tempo real
- [ ] Adicionar suporte a mais cidades
- [ ] Criar testes automatizados

## 📝 Notas de Desenvolvimento

### Ambiente de Desenvolvimento
- Use o modo de desenvolvimento do Vite para hot-reload no frontend
- Flask debug mode está habilitado para desenvolvimento
- MongoDB Atlas é usado em produção; considere MongoDB local para desenvolvimento

### Convenções de Código
- **Python**: PEP 8
- **TypeScript/Vue**: Padrões do Vue 3 Composition API
- **Commits**: Mensagens descritivas em português

## 🤝 Contribuindo

1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

## 📄 Licença

Este projeto é parte do PI5 (Projeto Integrador 5) e está disponível para fins educacionais.

## 👥 Autores

- Equipe PI5 - Living IA
- Repositório: [JONTK123/PI5-LivingIA](https://github.com/JONTK123/PI5-LivingIA)

## 📧 Contato

Para questões e suporte, abra uma issue no repositório do GitHub.

---

**Desenvolvido com ❤️ usando Python, Vue.js e Inteligência Artificial**
