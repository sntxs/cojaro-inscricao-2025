<template>
  <div class="page-container">
    <div class="container">
      <img class="logo" src="/src/components/assets/avivamento-biblico-logo.png" alt="Avivamento Bíblico Logo">

      <h1>Inscrição - Cojaro 2k25</h1>

      <form @submit.prevent="submitForm">
        <label for="nome">Nome Completo:</label>
        <input type="text" id="nome" name="Nome" v-model="formData.nome" required>

        <label for="estado">Estado:</label>
        <select id="estado" v-model="formData.estado" @change="atualizarCidades" name="Estado" required>
          <option value="">Selecione o Estado</option>
          <option v-for="estado in estadosCentroOeste" :key="estado" :value="estado">{{ estado }}</option>
        </select>

        <label for="cidade">Cidade:</label>
        <select id="cidade" v-model="formData.cidade" :disabled="!formData.estado" name="Cidade" required>
          <option value="">Selecione a Cidade</option>
          <option v-for="cidade in cidadesDisponiveis" :key="cidade" :value="cidade">{{ cidade }}</option>
        </select>

        <label for="nascimento">Data de Nascimento:</label>
        <input type="date" id="nascimento" name="Data de Nascimento" v-model="formData.nascimento" @change="atualizarTaxa" required>

        <label for="taxa">Tipo de Taxa:</label>
        <select id="taxa" v-model="formData.taxa" name="Tipo de Taxa" required>
          <option value="">Selecione</option>
          <option value="gratis" :disabled="isTaxaGratisDisabled">Até 5 anos - Grátis</option>
          <option value="meia" :disabled="isTaxaMeiaDisabled">6 a 10 anos - Meia Taxa</option>
          <option value="inteira" :disabled="isTaxaInteiraDisabled">11 anos ou mais - Taxa Inteira</option>
        </select>

        <label>Tem CPF?</label>
        <div>
          <button type="button" @click="setTemCPF(true)" :class="{ 'active': temCPF }">Sim</button>
          <button type="button" @click="setTemCPF(false)" :class="{ 'active': !temCPF }">Não</button>
        </div>

        <label for="cpf">CPF:</label>
        <input type="text" id="cpf" name="CPF" v-model="formData.cpf" :required="temCPF" :disabled="!temCPF" v-mask="'###.###.###-##'">

        <label for="telefone">Telefone:</label>
        <input type="tel" id="telefone" name="Telefone" v-model="formData.telefone" required v-mask="telefoneOptions.mask">

        <label for="email">E-mail:</label>
        <input type="email" id="email" name="E-mail" v-model="formData.email" required>

        <label for="lider">Nome do Líder:</label>
        <input type="text" id="lider" name="Nome do Líder" v-model="formData.lider" required>

        <label for="campo">Campo Eclesiástico:</label>
        <input type="text" id="campo" name="Campo Eclesiástico" v-model="formData.campo" required>

        <label for="pagamento">Forma de Pagamento:</label>
        <select id="pagamento" name="Forma de Pagamento" v-model="formData.pagamento" required>
          <option value="">Selecione</option>
          <option value="pix1x">PIX - 1x</option>
          <option value="pix2x">PIX - 2x</option>
          <option value="pix3x">PIX - 3x</option>
          <option value="credito">Cartão de Crédito</option>
          <option value="debito">Cartão de Débito</option>
        </select>

        <input type="hidden" name="Created" value="x-sheetmonkey-current-date-time" />
        <button class="btn-enviar" type="submit">Enviar Inscrição</button>
      </form>
    </div>

    <footer>
      <img class="footer-logo" src="/src/components/assets/ieab-logo.png"
        alt="Igreja Evangélica Avivamento Bíblico Logo">

      <p>&copy; 2025 Igreja Evangélica Avivamento Bíblico. Todos os direitos reservados.</p>

      <div class="social-media">
        <a href="https://www.facebook.com/cojarooficial" target="_blank" class="social-icon">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="currentColor" class="bi bi-facebook"
            viewBox="0 0 16 16">
            <path
              d="M16 8.049c0-4.446-3.582-8.05-8-8.05C3.58 0-.002 3.603-.002 8.05c0 4.017 2.926 7.347 6.75 7.951v-5.625h-2.03V8.05H6.75V6.275c0-2.017 1.195-3.131 3.022-3.131.876 0 1.791.157 1.791.157v1.98h-1.009c-.993 0-1.303.621-1.303 1.258v1.51h2.218l-.354 2.326H9.25V16c3.824-.604 6.75-3.934 6.75-7.951" />
          </svg>
        </a>

        <a href="https://www.instagram.com/cojarooficial?utm_source=ig_web_button_share_sheet&igsh=ZDNlZDc0MzIxNw=="
          target="_blank" class="social-icon">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="currentColor" class="bi bi-instagram"
            viewBox="0 0 16 16">
            <path
              d="M8 0C5.829 0 5.556.01 4.703.048 3.85.088 3.269.222 2.76.42a3.9 3.9 0 0 0-1.417.923A3.9 3.9 0 0 0 .42 2.76C.222 3.268.087 3.85.048 4.7.01 5.555 0 5.827 0 8.001c0 2.172.01 2.444.048 3.297.04.852.174 1.433.372 1.942.205.526.478.972.923 1.417.444.445.89.719 1.416.923.51.198 1.09.333 1.942.372C5.555 15.99 5.827 16 8 16s2.444-.01 3.298-.048c.851-.04 1.434-.174 1.943-.372a3.9 3.9 0 0 0 1.416-.923c.445-.445.718-.891.923-1.417.197-.509.332-1.09.372-1.942C15.99 10.445 16 10.173 16 8s-.01-2.445-.048-3.299c-.04-.851-.175-1.433-.372-1.941a3.9 3.9 0 0 0-.923-1.417A3.9 3.9 0 0 0 13.24.42c-.51-.198-1.092-.333-1.943-.372C10.443.01 10.172 0 7.998 0zm-.717 1.442h.718c2.136 0 2.389.007 3.232.046.78.035 1.204.166 1.486.275.373.145.64.319.92.599s.453.546.598.92c.11.281.24.705.275 1.485.039.843.047 1.096.047 3.231s-.008 2.389-.047 3.232c-.035.78-.166 1.203-.275 1.485a2.5 2.5 0 0 1-.599.919c-.28.28-.546.453-.92.598-.28.11-.704.24-1.485.276-.843.038-1.096.047-3.232.047s-2.39-.009-3.233-.047c-.78-.036-1.203-.166-1.485-.276a2.5 2.5 0 0 1-.92-.598c-.109-.281-.24-.705-.275-1.485-.038-.843-.046-1.096-.046-3.233s.008-2.388.046-3.231c.036-.78.166-1.204.276-1.486.145-.373.319-.64.599-.92s.546-.453.92-.598c.282-.11.705-.24 1.485-.276.738-.034 1.024-.044 2.515-.045zm4.988 1.328a.96.96 0 1 0 0 1.92.96.96 0 0 0 0-1.92m-4.27 1.122a4.109 4.109 0 1 0 0 8.217 4.109 4.109 0 0 0 0-8.217m0 1.441a2.667 2.667 0 1 1 0 5.334 2.667 2.667 0 0 1 0-5.334" />
          </svg>
        </a>

      </div>
    </footer>

    <!-- Modal de Erro -->
    <div v-if="showErrorModal" class="modal">
      <div class="modal-content">
        <span class="close" @click="closeErrorModal">&times;</span>
        <p>{{ errorMessage }}</p>
      </div>
    </div>

    <!-- Modal de Sucesso -->
    <div v-if="showSuccessModal" class="modal">
      <div class="modal-content">
        <p>Formulário enviado com sucesso! A página será recarregada em {{ countdown }} segundos.</p>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, reactive, computed } from 'vue';
import { mask } from 'vue-the-mask';

export default {
  directives: {
    mask
  },
  setup() {
    const formData = reactive({
      nome: '',
      estado: '',
      cidade: '',
      nascimento: '',
      taxa: '',
      cpf: '',
      telefone: '',
      email: '',
      lider: '',
      campo: '',
      pagamento: ''
    });

    const telefoneOptions = reactive({
      mask: '(##) #####-####'
    });

    const estadosCentroOeste = ['Goiás', 'Mato Grosso', 'Mato Grosso do Sul', 'Distrito Federal'];

    const cidadesPorEstado = {
      'Goiás': ['Goiânia', 'Anápolis', 'Aparecida de Goiânia', 'Rio Verde', 'Luziânia'],
      'Mato Grosso': ['Cuiabá', 'Várzea Grande', 'Rondonópolis', 'Sinop', 'Tangará da Serra'],
      'Mato Grosso do Sul': ['Campo Grande', 'Dourados', 'Três Lagoas', 'Corumbá', 'Ponta Porã'],
      'Distrito Federal': ['Brasília', 'Taguatinga', 'Ceilândia', 'Samambaia', 'Plano Piloto']
    };

    const cidadesDisponiveis = ref([]);
    const temCPF = ref(false);

    const showErrorModal = ref(false);
    const showSuccessModal = ref(false);
    const errorMessage = ref('');
    const countdown = ref(3);

    const atualizarCidades = () => {
      cidadesDisponiveis.value = formData.estado ? cidadesPorEstado[formData.estado] : [];
      formData.cidade = '';
    };

    const calcularIdade = (dataNascimento) => {
      if (!dataNascimento) return 0;
      const nascimento = new Date(dataNascimento);
      const hoje = new Date();
      let idade = hoje.getFullYear() - nascimento.getFullYear();
      const mes = hoje.getMonth() - nascimento.getMonth();
      if (mes < 0 || (mes === 0 && hoje.getDate() < nascimento.getDate())) {
        idade--;
      }
      return idade;
    };

    const atualizarTaxa = () => {
      const idade = calcularIdade(formData.nascimento);
      if (idade <= 5) {
        formData.taxa = 'gratis';
      } else if (idade >= 6 && idade <= 10) {
        formData.taxa = 'meia';
      } else if (idade >= 11) {
        formData.taxa = 'inteira';
      }
    };

    const isTaxaGratisDisabled = computed(() => formData.nascimento && calcularIdade(formData.nascimento) > 5);
    const isTaxaMeiaDisabled = computed(() => formData.nascimento && calcularIdade(formData.nascimento) < 6 || calcularIdade(formData.nascimento) > 10);
    const isTaxaInteiraDisabled = computed(() => formData.nascimento && calcularIdade(formData.nascimento) < 11);

    const setTemCPF = (value) => {
      temCPF.value = value;
      if (!value) {
        formData.cpf = '';
      }
    };

    const submitForm = async () => {
      if (validateForm()) {
        try {
          const response = await fetch('https://api.sheetmonkey.io/form/xunREX5PNLZ9rk1Qd8spWP', {
            method: 'POST',
            headers: {
              'Content-Type': 'application/json'
            },
            body: JSON.stringify(formData)
          });

          if (response.ok) {
            showSuccessModal.value = true;
            const interval = setInterval(() => {
              countdown.value--;
              if (countdown.value === 0) {
                clearInterval(interval);
                location.reload();
              }
            }, 1000);
          } else {
            throw new Error('Erro ao enviar o formulário.');
          }
        } catch (error) {
          errorMessage.value = error.message;
          showErrorModal.value = true;
        }
      } else {
        showErrorModal.value = true;
      }
    };

    const validateForm = () => {
      // Validação do nome
      if (!formData.nome.trim()) {
        errorMessage.value = 'Por favor, preencha o nome completo.';
        return false;
      }

      // Validação do estado e cidade
      if (!formData.estado || !formData.cidade) {
        errorMessage.value = 'Por favor, selecione o estado e a cidade.';
        return false;
      }

      // Validação da data de nascimento
      if (!formData.nascimento) {
        errorMessage.value = 'Por favor, informe a data de nascimento.';
        return false;
      }

      // Validação da taxa
      if (!formData.taxa) {
        errorMessage.value = 'Por favor, selecione o tipo de taxa.';
        return false;
      }

      // Validação do CPF
      if (temCPF.value && !validarCPF(formData.cpf)) {
        errorMessage.value = 'Por favor, informe um CPF válido.';
        return false;
      }

      // Validação do telefone
      if (!validarTelefone(formData.telefone)) {
        errorMessage.value = 'Por favor, informe um número de telefone válido.';
        return false;
      }

      // Validação do e-mail
      if (!validarEmail(formData.email)) {
        errorMessage.value = 'Por favor, informe um e-mail válido.';
        return false;
      }

      // Validação do nome do líder
      if (!formData.lider.trim()) {
        errorMessage.value = 'Por favor, informe o nome do líder.';
        return false;
      }

      // Validação do campo eclesiástico
      if (!formData.campo.trim()) {
        errorMessage.value = 'Por favor, informe o campo eclesiástico.';
        return false;
      }

      // Validação da forma de pagamento
      if (!formData.pagamento) {
        errorMessage.value = 'Por favor, selecione a forma de pagamento.';
        return false;
      }

      return true;
    };

    // Funções auxiliares de validação
    const validarCPF = (cpf) => {
      const cpfLimpo = cpf.replace(/[^\d]+/g, '');
      if (cpfLimpo.length !== 11 || /^(\d)\1{10}$/.test(cpfLimpo)) return false;
      
      let soma = 0;
      let resto;
      
      for (let i = 1; i <= 9; i++) 
        soma = soma + parseInt(cpfLimpo.substring(i-1, i)) * (11 - i);
      resto = (soma * 10) % 11;
      
      if ((resto === 10) || (resto === 11)) resto = 0;
      if (resto !== parseInt(cpfLimpo.substring(9, 10))) return false;
      
      soma = 0;
      for (let i = 1; i <= 10; i++) 
        soma = soma + parseInt(cpfLimpo.substring(i-1, i)) * (12 - i);
      resto = (soma * 10) % 11;
      
      if ((resto === 10) || (resto === 11)) resto = 0;
      if (resto !== parseInt(cpfLimpo.substring(10, 11))) return false;
      
      return true;
    };

    const validarTelefone = (telefone) => {
      const telefoneLimpo = telefone.replace(/\D/g, '');
      return telefoneLimpo.length >= 10 && telefoneLimpo.length <= 11;
    };

    const validarEmail = (email) => {
      const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      return re.test(email);
    };

    const closeErrorModal = () => {
      showErrorModal.value = false;
    };

    return {
      formData,
      telefoneOptions,
      submitForm,
      estadosCentroOeste,
      cidadesDisponiveis,
      atualizarCidades,
      atualizarTaxa,
      isTaxaGratisDisabled,
      isTaxaMeiaDisabled,
      isTaxaInteiraDisabled,
      temCPF,
      setTemCPF,
      showErrorModal,
      showSuccessModal,
      errorMessage,
      closeErrorModal,
      countdown
    };
  }
};
</script>

<style>
body {
  font-family: Arial, sans-serif;
  background-color: #f0f0f0;
  margin: 0;
  padding: 0;
  min-height: 100vh;
}

.page-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  padding: 50px 0;
}

h1 {
  text-transform: uppercase;
  padding: 10px 0 35px 0;
}

.btn-enviar {
  width: 50%;
  height: 50px;
  margin: auto;
  text-transform: uppercase;
  background-color: #3D418B;
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 16px;
  font-weight: bold;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 6px #2A2C5E;
  position: relative;
  top: 0;
}

.btn-enviar:hover {
  background-color: #4A4DA0;
  box-shadow: 0 4px #2A2C5E;
  top: 2px;
}

.btn-enviar:active {
  background-color: #3D418B;
  box-shadow: 0 0 #2A2C5E;
  top: 6px;
  transition: all 0.1s ease;
}

#pagamento {
  margin-bottom: 60px !important;
}

.logo {
  max-width: 200px;
  padding: 35px 0 35px 0;
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

footer {
  text-align: center;
  color: #555;
  margin-top: 30px;
}

.footer-logo {
  max-width: 150px;
  margin: 20px auto;
  background-color: transparent;
}

.social-media {
  margin-top: 10px;
}

.social-icon {
  color: #3D418B;
  text-decoration: none;
  margin: 0 10px;
  display: inline-block;
  transition: transform 0.3s ease-in-out;
  perspective: 1000px;
}

.social-icon:hover {
  transform: scale(1.2) rotate(10deg);
}

.social-icon:active {
  transform: scale(0.9) translateZ(-50px);
}

@media (max-width: 768px) {
  .container {
    padding: 20px;
    max-width: 90%;
  }

  input,
  select {
    font-size: 18px;
    padding: 12px;
  }

  .btn-enviar {
    width: 80%;
    padding: 15px;
    font-size: 18px;
  }

  footer {
    width: 100%;
    padding: 10px 0;
    background-color: transparent;
  }
}

button {
  padding: 10px 20px;
  margin: 0 5px 15px;
  background-color: #f0f0f0;
  border: 1px solid #ddd;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s;
}

button.active {
  background-color: #3D418B;
  color: white;
}

.modal {
  display: flex;
  justify-content: center;
  align-items: center;
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgba(0, 0, 0, 0.4);
}

.modal-content {
  background-color: #fefefe;
  margin: 15% auto;
  padding: 20px;
  border: 1px solid #888;
  width: 80%;
  max-width: 500px;
  text-align: center;
}

.close {
  color: #aaa;
  float: right;
  font-size: 28px;
  font-weight: bold;
}

.close:hover,
.close:focus {
  color: black;
  text-decoration: none;
  cursor: pointer;
}
</style>
