<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Implementação dos Estados de Bell com Qiskit</title>
</head>
<body>
    <h1>Implementação dos Estados de Bell com Qiskit</h1>

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


    Aqui está o texto formatado com as descrições e fórmulas dos estados de Bell:

---

<p><strong>O que são estados de Bell?</strong><br>
Estados de Bell são os quatro estados que podem ser criados quando dois qubits estão maximamente emaranhados. Os quatro estados são representados como:</p>

<p><img src="bell_states.png" alt="Estados de Bell"></p>

<p>Agora vamos analisar cada estado e ver como implementá-lo usando circuitos quânticos.</p>

<p><strong>O primeiro estado de Bell</strong> é incrivelmente fácil de implementar, pois pode ser criado usando um circuito de dois qubits consistindo de uma porta Hadamard e uma porta CNOT encontradas abaixo:</p>

<p><strong>Circuito para implementação do primeiro estado de Bell</strong></p>

<p>Isto irá emaranhar os dois qubits de modo que o estado combinado se torna:</p>

<p>\[
\frac{|00\rangle + |11\rangle}{\sqrt{2}}
\]</p>

<p>Agora vamos ver como o circuito realmente cria o primeiro estado de Bell. Como o circuito consiste em dois qubits ambos inicializados em \( |0\rangle \), o estado combinado inicial será:</p>

<p>\[
|00\rangle
\]</p>

<p>Agora que temos os dois qubits inicializados, podemos aplicar uma porta Hadamard ao nosso qubit de controle. Agora há um problema. Como aplicamos uma porta Hadamard ao nosso qubit de controle quando ele faz parte de um estado de 2 qubits? A melhor solução é expandir a matriz de portas Hadamard para que possamos aplicá-la ao nosso estado de dois qubits. Isso pode ser feito encontrando o produto de Kronecker da porta Hadamard e da porta identidade.</p>

<p>Lembre-se de que a matriz de portas de Hadamard é:</p>

\[ H = \frac{1}{\sqrt{2}} \begin{bmatrix} 1 & 1 \\ 1 & -1 \end{bmatrix} \]

<p>E a matriz de porta de identidade é:</p>

\[ I = \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix} \]

<p>Então o produto de Kronecker é:</p>

\[ H \otimes I = \frac{1}{\sqrt{2}} \begin{bmatrix} 1 & 0 & 1 & 0 \\ 0 & 1 & 0 & 1 \\ 1 & 0 & -1 & 0 \\ 0 & 1 & 0 & -1 \end{bmatrix} \]

<p>Em seguida, precisamos multiplicar a matriz acima pelo nosso estado de qubit inicializado:</p>

\[ \frac{1}{\sqrt{2}} \begin{bmatrix} 1 & 0 & 1 & 0 \\ 0 & 1 & 0 & 1 \\ 1 & 0 & -1 & 0 \\ 0 & 1 & 0 & -1 \end{bmatrix} \begin{bmatrix} 1 \\ 0 \\ 0 \\ 0 \end{bmatrix} = \frac{1}{\sqrt{2}} \begin{bmatrix} 1 \\ 0 \\ 1 \\ 0 \end{bmatrix} = \frac{|00\rangle + |11\rangle}{\sqrt{2}} \]

<p>Agora só precisamos aplicar a porta CNOT ao circuito multiplicando o estado acima pela matriz CNOT:</p>

\[ \frac{1}{\sqrt{2}} \begin{bmatrix} 1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 1 \\ 0 & 0 & 1 & 0 \end{bmatrix} \begin{bmatrix} 1 \\ 0 \\ 1 \\ 0 \end{bmatrix} = \frac{1}{\sqrt{2}} \begin{bmatrix} 1 \\ 0 \\ 0 \\ 1 \end{bmatrix} = \frac{|00\rangle + |11\rangle}{\sqrt{2}} \]

<p>O que finalmente nos dá o estado:</p>

\[ \frac{|00\rangle + |11\rangle}{\sqrt{2}} \]

<p>Agora que mostramos como o primeiro estado de Bell é criado, podemos passar para o segundo estado de Bell.</p>

<p>Lembre-se de que o <strong>segundo estado de Bell</strong> é:</p>

\[ \frac{|00\rangle - |11\rangle}{\sqrt{2}} \]

<p>Que é o mesmo que o primeiro estado de Bell, mas com uma fase negativa! Como tal, isso pode ser implementado facilmente usando o mesmo circuito do primeiro estado de Bell, mas com a adição de inicializar o primeiro qubit para \( |1\rangle \) com uma porta Pauli-X:</p>

<p><strong>Circuito para implementar o segundo estado de Bell</strong></p>

<p>O <strong>terceiro estado</strong> é um pouco diferente, pois apenas 1 qubit deve ser \( |1\rangle \) de modo que o estado combinado se torna:</p>

\[ \frac{|01\rangle + |10\rangle}{\sqrt{2}} \]

<p>Este estado pode ser criado usando um circuito muito semelhante aos dois últimos, mas com o segundo qubit inicializado como \( |1\rangle \) usando uma porta Pauli-X:</p>

<p><strong>Circuito para o terceiro estado de Bell</strong></p>

<p>O <strong>quarto estado de Bell</strong> é basicamente o mesmo que o terceiro estado de Bell, mas com uma fase negativa:</p>

\[ \frac{|01\rangle - |10\rangle}{\sqrt{2}} \]

<p>Isso pode ser implementado aplicando portas Pauli-Z a ambos os qubits:</p>

<p><strong>Circuito para o quarto estado de Bell</strong></p>

<p><strong>Como executar o programa:</strong></p>
<p>Copie e cole o código em um arquivo Python.</p>
<p>Insira seu token de API na parte <code>IBMQ.enable_account('Insira seu token aqui')</code>.</p>
<p>Salve e execute o arquivo.</p>

<p>Referências:</p>
<ul>
    <li><a href="https://quantum.ibm.com/">IBM Quantum</a></li>
    <li><a href="https://qiskit.org/">Qiskit</a></li>
</ul>

</body>
</html>
