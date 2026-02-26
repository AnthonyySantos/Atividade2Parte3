# Atividade2Parte3

OBS: Algumas partes tive auxilio da IA

QUESTAO 1 - [Questao1.js](https://github.com/user-attachments/files/25562962/Questao1.js)

    function formatarProdutos(json) {
  
      var dados = JSON.parse(json);
      var lista = [];
    
      for (var i = 0; i < dados.itens.length; i++) {
    
        var produto = dados.itens[i];
    
        var texto =
          produto.nome +
          " - R$ " +
          produto.preco.toFixed(2) +
          " (Categoria: " +
          produto.categoria +
          ")";
    
        lista.push(texto);
      }
    
      return lista;
    
QUESTAO 2 - [Questao2.js](https://github.com/user-attachments/files/25562976/Questao2.js)

    function analisarTexto(texto) {

      texto = texto.replace(".", "");
      texto = texto.replace(",", "");
    
      var palavras = texto.split(" ");
    
      var totalPalavras = palavras.length;
      var frequencia = {};
      var soma = 0;
    
      for (var i = 0; i < palavras.length; i++) {
    
        var palavra = palavras[i];
    
        soma += palavra.length;
    
        if (frequencia[palavra] == undefined) {
          frequencia[palavra] = 1;
        } else {
          frequencia[palavra]++;
        }
      }
    
      var listaFrequencia = [];
    
      for (var chave in frequencia) {
        listaFrequencia.push({
          palavra: chave,
          frequencia: frequencia[chave]
        });
      }
    
      var media = soma / totalPalavras;
    
      return {
        totalPalavras: totalPalavras,
        frequenciaPalavras: listaFrequencia,
        tamanhoMedioPalavras: media
      };
    }
   
QUESTAO 3 - [Questao3.js](https://github.com/user-attachments/files/25562990/Questao3.js)

       function normalizarUsuarios(json) {
      
            var usuarios = JSON.parse(json);
            var resultado = [];
          
            for (var i = 0; i < usuarios.length; i++) {
          
              var u = usuarios[i];
          
             
              var nome = u.nome.trim().toLowerCase();
              var partes = nome.split(" ");
              var nomeFinal = "";
          
              for (var j = 0; j < partes.length; j++) {
          
                var primeira = partes[j].charAt(0).toUpperCase();
                var resto = partes[j].slice(1);
          
                nomeFinal += primeira + resto + " ";
              }
          
              nomeFinal = nomeFinal.trim();
          
             
              var email = u.email.toLowerCase();
          
              var emailValido = false;
              if (email.indexOf("@") > 0 && email.indexOf(".") > 0) {
                emailValido = true;
              }
          
              
              var idade = Number(u.idade);
              var maiorDeIdade = false;
          
              if (idade >= 18) {
                maiorDeIdade = true;
              }
          
              resultado.push({
                nome: nomeFinal,
                email: email,
                emailValido: emailValido,
                idade: idade,
                maiorDeIdade: maiorDeIdade
              });
            }
          
            return resultado;
      }



QUESTAO 4 - [Questao4.js](https://github.com/user-attachments/files/25562992/Questao4.js)

    function sanitizarDados(dados) {

      var novo = {
        usuarios: [],
        metadata: {}
      };
    
      for (var i = 0; i < dados.usuarios.length; i++) {
  
      var x = dados.usuarios[i];
  
      var usuarioNovo = {};
  
      usuarioNovo.nome = x.nome;
  
     
      usuarioNovo.cpf = "***.***.***-" + x.cpf.slice(-2);
  
     
      usuarioNovo.cartaoCredito = "****-****-****-" + x.cartaoCredito.slice(-4);
  
     
      usuarioNovo.telefone = "(**) *****-" + x.telefone.slice(-4);
  
      novo.usuarios.push(usuarioNovo);
      }
     novo.metadata.ip = dados.metadata.ip;
      novo.metadata.token = dados.metadata.token.slice(0, 10) + "...";
    
      return novo;
    }
    
   
QUESTAO 5 - [Questao5.js](https://github.com/user-attachments/files/25563000/Questao5.js)

     function parseQueryString(query) {
    
        var objeto = {};
      
        
        var parametros = query.split("&");
      
       
        for (var i = 0; i < parametros.length; i++) {
      
          
          var partes = parametros[i].split("=");
      
          var chave = partes[0];
          var valor = partes[1];
      
         
         var numero = Number(valor);
  
        if (numero == numero) { 
          valor = numero;
        }
            
        
          objeto[chave] = valor;
        }
      
        return objeto;
    }

   
