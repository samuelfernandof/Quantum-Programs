
</head>
<body>
    <h2>Requisitos</h2>
    <ul>
        <li>Instalação do Qiskit: <code>!pip install qiskit</code></li>
        <li>Instalação do Qiskit IBM Runtime: <code>!pip install qiskit-ibm-runtime</code></li>
        <li>Instalação de ferramentas de visualização do Qiskit: <code>!pip install qiskit[visualization]</code></li>
        <li>Instalação do IPython Kernel: <code>python -m pip install ipykernel -U --force-reinstall</code></li>
    </ul>

    <h2>Configuração do Ambiente Virtual</h2>
    <p>Crie um ambiente virtual Python:</p>
    <code>python3 -m venv /caminho/para/seu/ambiente/virtual</code>

    <h2>Tutorial Atualizado do Qiskit</h2>
    <p>Para instruções detalhadas de instalação, consulte o <a href="https://docs.quantum.ibm.com/guides/install-qiskit">tutorial oficial do Qiskit</a>.</p>

    <h2>Criação de Conta IBM Quantum</h2>
    <p>Para criar uma conta IBM Quantum, visite <a href="https://quantum.ibm.com/">IBM Quantum</a>.</p>

    <h2>Criação de Conta na IBM Cloud</h2>
    <p>Para criar uma conta na IBM Cloud e uma instância de Quantum Computing, acesse <a href="https://cloud.ibm.com/catalog/services/quantum-computing">IBM Cloud</a>.</p>

    <h2>O que são estados de Bell?</h2>
    <p>Estados de Bell são os quatro estados que podem ser criados quando dois qubits estão maximamente emaranhados. Os quatro estados são representados como:</p>
    <img src="bell_states.png" alt="Estados de Bell">

    <h2>Implementação dos Estados de Bell</h2>

    <h3>Primeiro Estado de Bell</h3>
    <p>O primeiro estado de Bell pode ser facilmente implementado usando um circuito de dois qubits com uma porta Hadamard e uma porta CNOT:</p>
    <img src="circuit_bell_1.png" alt="Circuito para implementar o primeiro estado de Bell">
    <p>Isso emaranha os dois qubits de modo que o estado combinado se torna:</p>
    <p>\[ \frac{|00\rangle + |11\rangle}{\sqrt{2}} \]</p>
    <p>Para detalhes sobre como o circuito cria esse estado, consulte o arquivo Python.</p>

    <h3>Segundo Estado de Bell</h3>
    <p>O segundo estado de Bell é semelhante ao primeiro, mas com uma fase negativa. Pode ser implementado inicializando o primeiro qubit com \( |1\rangle \) usando uma porta Pauli-X:</p>
    <img src="circuit_bell_2.png" alt="Circuito para implementar o segundo estado de Bell">

    <h3>Terceiro Estado de Bell</h3>
    <p>O terceiro estado de Bell é criado com apenas um qubit em \( |1\rangle \):</p>
    <img src="circuit_bell_3.png" alt="Circuito para implementar o terceiro estado de Bell">

    <h3>Quarto Estado de Bell</h3>
    <p>O quarto estado de Bell é semelhante ao terceiro, mas com uma fase negativa em ambos os qubits:</p>
    <img src="circuit_bell_4.png" alt="Circuito para implementar o quarto estado de Bell">

    <h2>Como Executar o Programa</h2>
    <p>Copie e cole o código Python fornecido em um arquivo Python.</p>
    <p>Insira seu token de API na linha <code>IBMQ.enable_account('Insira seu token aqui')</code>.</p
