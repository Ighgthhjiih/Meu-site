<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Revisão de Provas ETEC</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f9f9f9;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            flex-direction: column;
        }
        .container {
            width: 80%;
            max-width: 600px;
            text-align: center;
            background-color: white;
            padding: 20px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            border-radius: 8px;
        }
        h1 {
            font-size: 2em;
            margin-bottom: 20px;
        }
        input[type="text"], input[type="password"] {
            width: 80%;
            padding: 10px;
            font-size: 1.2em;
            margin-bottom: 10px;
            border: 2px solid #ccc;
            border-radius: 5px;
        }
        button {
            padding: 10px 20px;
            font-size: 1.2em;
            border: none;
            background-color: #4CAF50;
            color: white;
            cursor: pointer;
            border-radius: 5px;
        }
        button:hover {
            background-color: #45a049;
        }
    </style>
</head>
<body>

    <!-- Tela de Login -->
    <div id="loginContainer" class="container">
        <h1>Área de Login</h1>
        <form id="loginForm" onsubmit="return handleLogin(event)">
            <input type="text" id="username" placeholder="Usuário" required><br>
            <input type="password" id="password" placeholder="Senha" required><br>
            <button type="submit">Entrar</button>
        </form>
        <div id="loginFeedback" style="margin-top: 20px;"></div>
    </div>

    <!-- Tela de Revisão (oculta até login) -->
    <div id="mainContainer" class="container" style="display: none;">
        <h1>Revisão de Provas ETEC</h1>
        <div class="question" id="question">Qual é a capital do Brasil?</div>
        <input type="text" id="userAnswer" placeholder="Digite sua resposta">
        <button onclick="checkAnswer()">Verificar Resposta</button>
        <div id="feedback" style="margin-top: 20px;"></div>
    </div>

    <script>
        // Dados de login (simulação, em um sistema real você usaria um backend)
        const validUsername = "admin";
        const validPassword = "12345";

        // Perguntas e Respostas
        const questions = [
            { question: 'Qual é a capital do Brasil?', answer: 'brasilia' },
            { question: 'Quem foi o primeiro presidente do Brasil?', answer: 'marechal deodoro' },
            { question: 'Qual é a fórmula da água?', answer: 'h2o' },
            { question: 'O que significa "HTML"?', answer: 'hypertext markup language' },
            { question: 'Qual é o maior planeta do sistema solar?', answer: 'jupiter' },
            { question: 'Quantos estados o Brasil tem?', answer: '26' },
            { question: 'Em que ano o Brasil foi descoberto?', answer: '1500' },
            { question: 'Quem escreveu "Dom Casmurro"?', answer: 'machado de assis' },
            { question: 'Qual é a capital da França?', answer: 'paris' },
            { question: 'Qual o nome do primeiro homem a pisar na Lua?', answer: 'neil armstrong' },
            { question: 'Quem pintou a Mona Lisa?', answer: 'leonardo da vinci' },
            { question: 'Qual a principal língua falada no Japão?', answer: 'japones' },
            { question: 'Qual o nome do maior rio do mundo?', answer: 'amazonas' },
            { question: 'Quem inventou a lâmpada elétrica?', answer: 'thomas edison' },
            { question: 'Qual é a moeda oficial dos Estados Unidos?', answer: 'dolar' },
            { question: 'Qual é o nome do maior oceano do mundo?', answer: 'pacifico' },
            { question: 'O que é a fotossíntese?', answer: 'processo em que as plantas produzem energia a partir da luz' },
            { question: 'Em que ano terminou a Segunda Guerra Mundial?', answer: '1945' },
            { question: 'Qual é a fórmula da velocidade média?', answer: 'distancia/tempo' },
            { question: 'O que significa a sigla "ONU"?', answer: 'organização das nações unidas' },
            { question: 'Qual o maior deserto do mundo?', answer: 'saara' },
            { question: 'Quem é o autor de "O Primo Basílio"?', answer: 'josé de alencar' },
            { question: 'Qual o nome do livro mais vendido do mundo, depois da Bíblia?', answer: 'o pequeno principe' },
            { question: 'Quantos continentes existem no planeta?', answer: '7' },
            { question: 'Qual o elemento químico com o símbolo "O"?', answer: 'oxigenio' },
            { question: 'Qual a fórmula química do sal de cozinha?', answer: 'na cl' },
            { question: 'Qual é o nome da maior floresta tropical do mundo?', answer: 'floresta amazonica' }
            // Adicione mais perguntas aqui
        ];

        let currentQuestion = 0;

        // Função de login
        function handleLogin(event) {
            event.preventDefault();
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;

            if (username === validUsername && password === validPassword) {
                document.getElementById('loginContainer').style.display = 'none';
                document.getElementById('mainContainer').style.display = 'block';
                loadNextQuestion();
            } else {
                document.getElementById('loginFeedback').innerText = 'Usuário ou senha inválidos. Tente novamente.';
                document.getElementById('loginFeedback').style.color = 'red';
            }
        }

        // Função para carregar a próxima pergunta
        function loadNextQuestion() {
            currentQuestion = (currentQuestion + 1) % questions.length;
            document.getElementById('question').innerText = questions[currentQuestion].question;
            document.getElementById('userAnswer').value = '';
            document.getElementById('feedback').innerHTML = '';
        }

        // Função para verificar a resposta do usuário
        function checkAnswer() {
            const userAnswer = document.getElementById('userAnswer').value.toLowerCase();
            const correctAnswer = questions[currentQuestion].answer;
            const feedback = document.getElementById('feedback');

            if (userAnswer === correctAnswer) {
                feedback.innerHTML = 'Resposta Correta!';
                feedback.style.color = 'green';
                setTimeout(loadNextQuestion, 2000); // Carregar próxima pergunta após 2 segundos
            } else {
                feedback.innerHTML = 'Resposta Errada. Tente novamente!';
                feedback.style.color = 'red';
            }
        }
    </script>

</body>
</html>
