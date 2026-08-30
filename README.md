// ==========================================
// PC VIRTUAL BUILDER
// RTX 5070 12 GB
// Somente JavaScript
// ==========================================

const componentes = {

    cpu: {
        nome: "Ryzen 5 7600",
        preco: 1050,
        socket: "AM5",
        desempenho: 85
    },

    gpu: {
        nome: "RTX 5070 12 GB",
        preco: 5000,
        vram: 12,
        desempenho: 170,
        consumo: 250
    },

    ram: {
        nome: "32 GB DDR5",
        preco: 700,
        capacidade: 32,
        tipo: "DDR5"
    },

    placaMae: {
        nome: "B650 AM5",
        preco: 800,
        socket: "AM5",
        ram: "DDR5"
    },

    armazenamento: {
        nome: "SSD NVMe 1 TB",
        preco: 400,
        capacidade: "1 TB"
    },

    fonte: {
        nome: "750 W",
        preco: 550,
        potencia: 750
    },

    gabinete: {
        nome: "Gabinete Gamer Airflow",
        preco: 400
    }
};


// ==========================================
// JOGOS
// ==========================================

const jogos = [
    "GTA V",
    "Red Dead Redemption 2",
    "Resident Evil 2 Remake",
    "Resident Evil 3 Remake",
    "Resident Evil 4 Remake",
    "Metal Gear Solid V",
    "Cyberpunk 2077",
    "Forza Horizon 5",
    "Uncharted: Legacy of Thieves",
    "Hogwarts Legacy",
    "The Last of Us Part I",
    "Alan Wake 2"
];


// ==========================================
// CRIAR INTERFACE
// ==========================================

document.body.innerHTML = "";

document.body.style.margin = "0";
document.body.style.background = "#080b12";
document.body.style.color = "white";
document.body.style.fontFamily = "Arial";


// ==========================================
// CABEÇALHO
// ==========================================

const titulo = document.createElement("h1");

titulo.textContent = "🖥️ PC Virtual Builder";

titulo.style.textAlign = "center";
titulo.style.padding = "25px";
titulo.style.background = "#111827";

document.body.appendChild(titulo);


// ==========================================
// CONTAINER
// ==========================================

const container = document.createElement("div");

container.style.maxWidth = "1000px";
container.style.margin = "auto";
container.style.padding = "20px";

document.body.appendChild(container);


// ==========================================
// PC VIRTUAL
// ==========================================

const pc = document.createElement("div");

pc.style.background = "#111827";
pc.style.border = "2px solid #334155";
pc.style.borderRadius = "15px";
pc.style.padding = "25px";

container.appendChild(pc);


// ==========================================
// GABINETE
// ==========================================

const gabinete = document.createElement("div");

gabinete.textContent = "🖥️ GABINETE";

gabinete.style.background = "#020617";
gabinete.style.border = "3px solid #475569";
gabinete.style.borderRadius = "12px";
gabinete.style.padding = "20px";

pc.appendChild(gabinete);


// ==========================================
// COMPONENTES VISUAIS
// ==========================================

function criarPeca(nome, emoji) {

    const peca = document.createElement("div");

    peca.textContent = emoji + " " + nome;

    peca.style.background = "#1e293b";
    peca.style.border = "1px solid #475569";
    peca.style.borderRadius = "8px";
    peca.style.padding = "15px";
    peca.style.marginTop = "10px";

    gabinete.appendChild(peca);

    return peca;
}


const cpuVisual =
    criarPeca(componentes.cpu.nome, "🧠");

const gpuVisual =
    criarPeca(componentes.gpu.nome, "🎮");

const ramVisual =
    criarPeca(componentes.ram.nome, "💾");

const placaVisual =
    criarPeca(componentes.placaMae.nome, "🧩");

const fonteVisual =
    criarPeca(componentes.fonte.nome, "🔌");

const armazenamentoVisual =
    criarPeca(componentes.armazenamento.nome, "💽");


// ==========================================
// PREÇO
// ==========================================

const precoTitulo =
    document.createElement("h2");

precoTitulo.textContent = "💰 Preço total";

container.appendChild(precoTitulo);


const preco =
    document.createElement("h1");

preco.style.color = "#4ade80";

container.appendChild(preco);


// ==========================================
// CALCULAR PREÇO
// ==========================================

function calcularPreco() {

    let total = 0;

    total += componentes.cpu.preco;
    total += componentes.gpu.preco;
    total += componentes.ram.preco;
    total += componentes.placaMae.preco;
    total += componentes.armazenamento.preco;
    total += componentes.fonte.preco;
    total += componentes.gabinete.preco;

    preco.textContent =
        total.toLocaleString(
            "pt-BR",
            {
                style: "currency",
                currency: "BRL"
            }
        );
}


// ==========================================
// COMPATIBILIDADE
// ==========================================

const compatibilidade =
    document.createElement("div");

compatibilidade.style.background = "#0f172a";
compatibilidade.style.padding = "20px";
compatibilidade.style.borderRadius = "10px";
compatibilidade.style.marginTop = "20px";

container.appendChild(compatibilidade);


function verificarCompatibilidade() {

    let resultado = "";

    if (
        componentes.cpu.socket ===
        componentes.placaMae.socket
    ) {

        resultado +=
            "✅ CPU e placa-mãe compatíveis<br>";

    } else {

        resultado +=
            "❌ CPU incompatível com a placa-mãe<br>";

    }


    if (
        componentes.ram.tipo ===
        componentes.placaMae.ram
    ) {

        resultado +=
            "✅ Memória RAM compatível<br>";

    } else {

        resultado +=
            "❌ Memória RAM incompatível<br>";

    }


    if (
        componentes.fonte.potencia >= 750
    ) {

        resultado +=
            "✅ Fonte adequada para a RTX 5070<br>";

    } else {

        resultado +=
            "⚠️ Fonte abaixo do recomendado<br>";

    }


    compatibilidade.innerHTML =
        "<h2>🔍 Compatibilidade</h2>" +
        resultado;

}


// ==========================================
// DESEMPENHO
// ==========================================

const desempenhoTitulo =
    document.createElement("h2");

desempenhoTitulo.textContent =
    "🎮 Desempenho estimado";

container.appendChild(desempenhoTitulo);


const desempenho =
    document.createElement("div");

container.appendChild(desempenho);


function calcularFPS() {

    desempenho.innerHTML = "";

    const cpu =
        componentes.cpu.desempenho;

    const gpu =
        componentes.gpu.desempenho;

    const poder =
        (cpu * 0.35) +
        (gpu * 0.65);


    jogos.forEach((jogo, index) => {

        const baseFPS = [
            180,
            100,
            170,
            155,
            120,
            180,
            100,
            125,
            95,
            90,
            80,
            65
        ];

        let fps =
            baseFPS[index] *
            (poder / 100);


        fps = Math.round(fps);


        const jogoDiv =
            document.createElement("div");

        jogoDiv.style.background =
            "#0f172a";

        jogoDiv.style.border =
            "1px solid #334155";

        jogoDiv.style.borderRadius =
            "10px";

        jogoDiv.style.padding =
            "15px";

        jogoDiv.style.marginBottom =
            "10px";


        jogoDiv.innerHTML = `
            <strong>${jogo}</strong>
            <br>
            <span style="color:#4ade80;font-size:20px">
                ${fps} FPS
            </span>
        `;


        desempenho.appendChild(jogoDiv);

    });

}


// ==========================================
// BOTÃO
// ==========================================

const botao =
    document.createElement("button");

botao.textContent =
    "🔄 Atualizar PC";

botao.style.width = "100%";
botao.style.padding = "15px";
botao.style.marginTop = "20px";
botao.style.background = "#2563eb";
botao.style.color = "white";
botao.style.border = "0";
botao.style.borderRadius = "8px";
botao.style.fontSize = "17px";
botao.style.cursor = "pointer";

container.appendChild(botao);


botao.onclick = function() {

    calcularPreco();

    verificarCompatibilidade();

    calcularFPS();

};


// ==========================================
// INICIALIZAR
// ==========================================

calcularPreco();

verificarCompatibilidade();

calcularFPS();


// ==========================================
// INFORMAÇÕES DA RTX 5070
// ==========================================

const info =
    document.createElement("div");

info.style.marginTop = "25px";
info.style.padding = "20px";
info.style.background = "#111827";
info.style.borderRadius = "10px";

info.innerHTML = `
    <h2>🎮 RTX 5070</h2>

    <p>
        <strong>VRAM:</strong>
        ${componentes.gpu.vram} GB
    </p>

    <p>
        <strong>Consumo estimado:</strong>
        ${componentes.gpu.consumo} W
    </p>

    <p>
        <strong>Fonte selecionada:</strong>
        ${componentes.fonte.potencia} W
    </p>

    <p>
        <strong>CPU:</strong>
        ${componentes.cpu.nome}
    </p>

    <p>
        <strong>RAM:</strong>
        ${componentes.ram.nome}
    </p>
`;

container.appendChild(info);


// ==========================================
// FINAL
// ==========================================

console.log("PC Virtual iniciado!");
console.log("GPU:", componentes.gpu.nome);
console.log("VRAM:", componentes.gpu.vram + " GB");
console.log("CPU:", componentes.cpu.nome);
console.log("RAM:", componentes.ram.nome);
