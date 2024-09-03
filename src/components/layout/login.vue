<template>
    <div class="container">

        <img class="logo" src="/src/components/assets/avivamento-biblico-logo.jpg" alt="Avivamento Bíblico Logo">

        <h1>Inscrição - Cojaro</h1>
        <form id="inscricaoForm">
            <label for="nome">Nome Completo:</label>
            <input type="text" id="nome" name="nome" required pattern="^[A-Za-zÀ-ÿ]+(?: [A-Za-zÀ-ÿ]+){2,}$">

            <label for="cidade">Cidade:</label>

            <input type="text" id="cidade" name="cidade" required>

            <label for="nascimento">Data de Nascimento:</label>
            <input type="date" id="nascimento" name="nascimento" required>

            <label for="taxa">Tipo de Taxa:</label>
            <select id="taxa" name="taxa" required>
                <option value="">Selecione</option>
                <option value="gratis">Até 5 anos - Grátis</option>
                <option value="meia">6 a 10 anos - Meia Taxa</option>
                <option value="inteira">11 anos ou mais - Taxa Inteira</option>
            </select>

            <label for="cpf">CPF:</label>
            <input type="text" id="cpf" name="cpf" required>

            <label for="telefone">Telefone:</label>
            <input type="tel" id="telefone" name="telefone" required>

            <label for="email">E-mail:</label>
            <input type="email" id="email" name="email" required>

            <label for="lider">Nome do Líder:</label>
            <input type="text" id="lider" name="lider" required>

            <label for="campo">Campo Eclesiástico:</label>
            <input type="text" id="campo" name="campo" required>

            <label for="pagamento">Forma de Pagamento:</label>
            <select id="pagamento" name="pagamento" required>
                <option value="">Selecione</option>
                <option value="pix1x">PIX - 1x</option>
                <option value="pix2x">PIX - 2x</option>
                <option value="pix3x">PIX - 3x</option>
                <option value="credito">Cartão de Crédito</option>
                <option value="debito">Cartão de Débito</option>
            </select>


            <button type="submit">Enviar Inscrição</button>
        </form>
    </div>

    <footer>
        <p>&copy; 2025 Igreja Evangélica Avivamento Bíblico. Todos os direitos reservados.</p>
        <div class="social-media">
            <a href="#" target="_blank">Facebook</a>
            <a href="https://www.instagram.com/cojarooficial?utm_source=ig_web_button_share_sheet&igsh=ZDNlZDc0MzIxNw=="
                target="_blank">Instagram</a>
        </div>
    </footer>
</template>

<style>
body {
    font-family: Arial, sans-serif;
    background-color: #f0f0f0;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    margin: 0;
    padding: 50px 0;
}

.logo {
    max-width: 200px;
    margin: auto;
    display: block;
}

.container {
    background-color: #ffffff;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    padding: 30px;
    width: 100%;
    max-width: 500px;
}

h1 {
    text-align: center;
    color: #333;
    margin-bottom: 20px;
}

form {
    display: flex;
    flex-direction: column;
}

label {
    margin-bottom: 5px;
    color: #555;
}

input,
select {
    padding: 10px;
    margin-bottom: 15px;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-size: 16px;
}

button {
    background-color: #3D418B;
    color: white;
    padding: 12px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 16px;
    transition: 0.3s;
}

button:hover {
    transition: 0.3s;
}

footer {
    margin-top: 30px;
    text-align: center;
    color: #555;
}

.social-media {
    margin-top: 10px;
}

.social-media a {
    color: #3D418B;
    text-decoration: none;
    margin: 0 10px;
}
</style>
