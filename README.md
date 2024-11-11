<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>SignUp - RocketMovies</title>
  <link rel="stylesheet" href="styles/index.css">
</head>
<body>
  <div class="container">
    <div class="form-container">
      <h1>Resident´s portal</h1>
      <p>Cadastro de moradores com indicadores sociais.</p>
      <h2>Crie sua conta</h2>

      <form id="signup-form">
        <div class="input-wrapper">
          <input type="text" placeholder="Nome" id="name" required>
          <span class="icon">&#x1F464;</span>
        </div>

        <div class="input-wrapper">
          <input type="email" placeholder="E-mail" id="email" required>
          <span class="icon">&#x2709;</span>
        </div>

        <div class="input-wrapper">
          <input type="password" placeholder="Senha" id="password" required>
          <span class="icon">&#x1F512;</span>
        </div>

        <div class="input-wrapper">
          <input type="password" placeholder="Confirmar Senha" id="confirm-password" required>
          <span class="icon">&#x1F512;</span>
        </div>

        <button type="submit">Cadastrar</button>
      </form>

      <a href="index.html">Já tem uma conta? Faça login</a>
    </div>
  </div>

  <script>
    // Captura o formulário de cadastro
    const form = document.getElementById('signup-form');
    form.addEventListener('submit', async function(e) {
      e.preventDefault();

      const nome = document.getElementById('name').value;
      const email = document.getElementById('email').value;
      const senha = document.getElementById('password').value;
      const confirmSenha = document.getElementById('confirm-password').value;

      // Enviar os dados para o backend
      const response = await fetch('http://localhost:3000/cadastro', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify({ nome, email, senha, confirmSenha })
      });

      const data = await response.json();

      if (response.ok) {
        alert(data.message);
        window.location.href = 'index.html';  // Redirecionar para a página de login
      } else {
        alert(data.message);
      }
    });
  </script>
</body>
</html>

