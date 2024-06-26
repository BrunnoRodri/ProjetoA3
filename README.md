# Gerenciador de Livros Online

Este é um projeto de Gerenciador de Livros Online, onde os usuários podem explorar, adicionar livros ao carrinho, realizar compras com pagamento seguro via Stripe e fazer reservas de livros. Administradores têm acesso a funcionalidades para gerenciar o estoque e usuários podem recuperar senhas via e-mail. O sistema garante uma experiência de compra fácil e segura, com atualizações automáticas de estoque após cada compra.

## Funcionalidades

- **Exploração de Livros:** Os usuários podem navegar pela lista de livros disponíveis, visualizando detalhes como nome, autor, preço e quantidade em estoque.
- **Carrinho de Compras:** Adicione livros ao carrinho e veja todos os itens selecionados com suas quantidades e preços.
- **Finalização de Compra:** Realize pagamentos seguros via Stripe, com confirmação de pagamento e atualização automática do estoque.
- **Reservas de Livros:** Se um livro não estiver em estoque, os usuários podem reservá-lo e receber uma notificação quando ele estiver disponível.
- **Login e Registro:** Usuários podem se registrar e fazer login para acessar a loja.
- **Recuperação de Senha:** Recuperação de senha via e-mail.
- **Administração:** Administradores podem adicionar, remover e atualizar livros no estoque.

## Bibliotecas Utilizadas

### Backend

- Express: Framework para Node.js utilizado para criar a estrutura do servidor e definir rotas.
- MySQL2: Biblioteca para conectar e interagir com o banco de dados MySQL.
- Express-Session: Middleware para gerenciar sessões de usuário.
- Nodemailer: Utilizado para enviar e-mails de recuperação de senha.
- Bcrypt: Biblioteca para hashing de senhas, garantindo a segurança dos dados de login.
- Stripe: Biblioteca para processar pagamentos online de forma segura.

### Frontend

- HTML/CSS: Estrutura e estilização das páginas da loja.
- JavaScript: Scripts para interações dinâmicas e comunicação com o backend.
- Stripe.js: Biblioteca para integração com o serviço de pagamentos Stripe.

## Instalação

1. Clone o repositório:
   ```bash
   git clone https://github.com/seu-usuario/seu-repositorio.git
   cd seu-repositorio
   ```

2. Instale as dependências:
   ```bash
   npm install express mysql2 express-session path nodemailer bcrypt dotenv stripe
   ```

3. Configure as variáveis de ambiente no arquivo `.env`:
   ```
   STRIPE_SECRET_KEY=your_stripe_secret_key
   STRIPE_PUBLIC_KEY=your_stripe_public_key
   EMAIL_USER=your_email@gmail.com
   EMAIL_PASS=your_email_password
   ```

4. Inicie o servidor:
   ```bash
   node server.js
   ```

## Uso

- Iniciar o servidor: Acesse `http://localhost:3000` no seu navegador.
- Navegar na loja: Explore os livros disponíveis e adicione-os ao carrinho.
- Realizar compras: Finalize a compra utilizando a integração com Stripe.
- Gerenciar estoque: Acesse o painel de administração para adicionar, remover e atualizar livros.

## Contribuição

Se você quiser contribuir com o projeto, siga estas etapas:

1. Faça um fork do repositório.
2. Crie uma branch para sua feature (`git checkout -b feature/nova-feature`).
3. Commit suas alterações (`git commit -am 'Adicionei nova feature'`).
4. Faça um push para a branch (`git push origin feature/nova-feature`).
5. Crie um Pull Request.

## Acessar
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=
//suasenha
DB_NAME=
//sua database

STRIPE_SECRET_KEY=
//sk_test_51PHYcWEgxOfM3CbTqok5nxlgYNVNYFrIRPsJBgiFq7ICx5UaCLVSZFLvhfFdThypQyV0ducA7LG0I49Or4QCZ8oW00T9SBMgiX
STRIPE_PUBLIC_KEY=
//pk_test_51PHYcWEgxOfM3CbTWufDz6MOtC4Zg9B8HknIpVi6Kmk5jDGpGWBe8CIHdbdTVmQsSIzU4gocb3hT8R64xSwwll9a00qeqyhDPh

EMAIL_USER=Laurasernin@gmail.com
EMAIL_PASSWORD=
//crcntzbapfadzibo

CREATE TABLE reservas (
    id INT AUTO_INCREMENT PRIMARY KEY,
    livro_id INT,
    email VARCHAR(100),
    FOREIGN KEY (livro_id) REFERENCES livros(id)
);


CREATE TABLE senha_reset (
    id INT AUTO_INCREMENT PRIMARY KEY,
    email VARCHAR(100),
    token VARCHAR(255),
    expiracao DATETIME
);


CREATE TABLE livros (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100),
    autor VARCHAR(100),
    preco DECIMAL(10, 2),
    estoque INT
);



CREATE TABLE adm (
    id INT AUTO_INCREMENT PRIMARY KEY,
    administrador VARCHAR(100),
    senha VARCHAR(255)
);



CREATE TABLE clientes (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100),
    cpf VARCHAR(14),
    cep VARCHAR(9),
    senha VARCHAR(255),
    cidade VARCHAR(100),
    email VARCHAR(100)
);
## Licença

Este projeto está licenciado sob a Licença MIT - veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---