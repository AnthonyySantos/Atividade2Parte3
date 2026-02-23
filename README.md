# Atividade2Parte3

OBS: Fiz as questões com auxilio da IA (n tava conseguindo raciocinar)

QUESTAO 1
[Questao1.js](https://github.com/user-attachments/files/25501003/Questao1.js)
  
    function formatarProdutos(json) {
        const dados = JSON.parse(json); 
        const itens = dados.items;

    return itens.map(item => {
        const precoFormatado = item.preco.toFixed(2).replace(".", ",");
        return `${item.nome} - R$ ${precoFormatado} (Categoria: ${item.categoria})`;
    });
    }

    const produtosJSON = `{
    "items": [
        {
            "id": 1,
            "nome": "Notebook Gamer",
            "preco": 2999.99,
            "categoria": "eletronicos",
            "tags": ["tecnologia", "computacao", "gamer"]
        },
        {
            "id": 2,
            "nome": "Mesa Escritório",
            "preco": 450.50,
            "categoria": "moveis",
            "tags": ["escritorio", "madeira", "profissional"]
        }
    ]
    }`;
    
    console.log(formatarProdutos(produtosJSON));


QUESTAO 2 
[Questao2.js](https://github.com/user-attachments/files/25501042/Questao2.js)

    [Uploading Questao function analisarTexto(texto) {
    const palavras = texto
        .toLowerCase()
        .replace(/[^\wÀ-ÿ ]+/g, "") 
        .split(/\s+/)
        .filter(p => p.length > 0);

    const totalPalavras = palavras.length;


    const mapa = {};
    palavras.forEach(p => {
        mapa[p] = (mapa[p] || 0) + 1;
    });

    const frequenciaPalavras = Object.keys(mapa).map(p => ({
        palavra: p,
        frequencia: mapa[p]
    }));


    const somaTamanhos = palavras.reduce((acc, p) => acc + p.length, 0);
    const tamanhoMedioPalavras = somaTamanhos / totalPalavras;

    return {
        totalPalavras,
        frequenciaPalavras,
        tamanhoMedioPalavras: tamanhoMedioPalavras.toFixed(2)
    };
    }
    
    const texto = "JavaScript é uma linguagem de programação. JavaScript é versátil e JavaScript é poderoso.";
    
    console.log(analisarTexto(texto));2.js…]()

QUESTAO 3
[Questao3.js](https://github.com/user-attachments/files/25501113/Questao3.js)

    [Uploadingconst usuariosJSON = `[
    {"nome": "  carlos silva  ", "email": "CARLOS@EMAIL.COM", "idade": "25"},
    {"nome": "   MARIA", "email": "maria@email.com", "idade": "30"},
    {"nome": "João Santos", "email": "joao@email.com", "idade": "17"}
    ]`;


    function normalizarUsuarios(json) {
        const usuarios = JSON.parse(json);

    return usuarios.map(u => {

        const nomeNormalizado = u.nome
            .trim()
            .toLowerCase()
            .split(" ")
            .filter(n => n.length > 0) 
            .map(n => n[0].toUpperCase() + n.substring(1))
            .join(" ");


        const emailNormalizado = u.email.toLowerCase();


        const idadeNumero = Number(u.idade);
        const maiorDe18 = idadeNumero >= 18;

        return {
            nome: nomeNormalizado,
            email: emailNormalizado,
            idade: idadeNumero,
            maiorDe18: maiorDe18
        };
    });
    }
    
    console.log(normalizarUsuarios(usuariosJSON));

QUESTAO 4
[Questao4.js](https://github.com/user-attachments/files/25501144/Questao4.js)

    [Uploading Questaoconst dadosSensiveis = {
    usuarios: [
        {
            cpf: "123.456.789-00",
            cartaoCredito: "5555-6666-7777-8888",
            telefone: "(11) 99999-9999",
            nome: "Fulano de Tal"
        }
    ],
    metadata: {
        ip: "192.168.1.100",
        token: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9"
    }
    };


    function sanitizarDados(dados) {
        return {
            usuarios: dados.usuarios.map(u => ({
                ...u,
                cpf: u.cpf.replace(/\d{3}\.\d{3}\.\d{3}/, "***.***.***"),
                cartaoCredito: u.cartaoCredito.replace(/\d{4}-\d{4}-\d{4}/, "****-****-****"),
                telefone: u.telefone.replace(/\(\d{2}\)\s\d{5}/, match => {
                    const ddd = match.slice(0, 4); 
                    return `${ddd}*****`;
                }),
            })),
            metadata: {
                ...dados.metadata,
                token: dados.metadata.token.slice(0, 10) + "..."
            }
        };
    }
    
    
    console.log(sanitizarDados(dadosSensiveis));4.js…]()

QUESTAO 5
[Questao5.js](https://github.com/user-attachments/files/25501164/Questao5.js)

    [Uploading Questafunction parseQueryString(query) {
        const partes = query.split("&");

    const resultado = {};

    partes.forEach(par => {
        const [chave, valor] = par.split("=");

        const numero = Number(valor);
        resultado[chave] = isNaN(numero) ? valor : numero;
    });

    return resultado;
    }
    
    const queryString = "categoria=eletronicos&preco=500&marca=samsung&avaliacao=4.5";
    
    console.log(parseQueryString(queryString));
    


