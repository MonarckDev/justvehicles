<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title id="siteTitle">Just Vehicles</title>
  <style>
    /* Reset e base */
    * {
      box-sizing: border-box;
    }
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: #121917;
      margin: 0;
      padding: 0;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      color: #d1f2a5;
    }

    header {
      background: #0f1a13;
      color: #d1f2a5;
      padding: 15px 20px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 15px;
      flex-wrap: wrap;
      border-bottom: 2px solid #34d058;
      box-shadow: 0 2px 10px rgba(52, 208, 88, 0.4);
      position: relative;
      z-index: 10;
    }
    header img {
      height: 50px;
      flex-shrink: 0;
      filter: drop-shadow(0 0 3px #34d058);
    }
    .site-name {
      font-weight: 700;
      font-size: 1.6rem;
      user-select: none;
    }
    .search-bar {
      padding: 10px 15px;
      width: 250px;
      max-width: 100%;
      border: none;
      border-radius: 25px;
      font-size: 1rem;
      background-color: #1f2a20;
      color: #d1f2a5;
      box-shadow: inset 0 0 8px #34d058;
      transition: box-shadow 0.3s ease;
    }
    .search-bar::placeholder {
      color: #8abf7a;
    }
    .search-bar:focus {
      outline: none;
      box-shadow: 0 0 12px #34d058;
      background-color: #18241a;
    }

    /* Botão 3 pontinhos fixo */
    #btnConfig {
      position: fixed;
      top: 20px;
      right: 20px;
      width: 40px;
      height: 40px;
      background: #34d058;
      border-radius: 50%;
      cursor: pointer;
      box-shadow: 0 0 10px #34d058cc;
      display: none; /* só aparece para adm e ceo */
      flex-direction: column;
      justify-content: space-around;
      align-items: center;
      padding: 6px 0;
      z-index: 1000;
    }
    #btnConfig span {
      display: block;
      width: 6px;
      height: 6px;
      background-color: #121917;
      border-radius: 50%;
      box-shadow: 0 0 4px #121917;
    }
    #btnConfig:hover {
      background: #2fb44d;
      box-shadow: 0 0 18px #2fb44dcc;
    }

    /* Menu lateral de configurações */
    #menuLateral {
      position: fixed;
      top: 0;
      right: -300px;
      width: 300px;
      height: 100vh;
      background-color: #1b2a1f;
      box-shadow: -4px 0 15px rgba(52, 208, 88, 0.7);
      transition: right 0.3s ease;
      z-index: 999;
      padding: 20px;
      display: flex;
      flex-direction: column;
      gap: 20px;
      color: #d1f2a5;
      overflow-y: auto;
    }
    #menuLateral.ativo {
      right: 0;
    }
    #menuLateral h2 {
      margin: 0;
      font-size: 1.5rem;
      border-bottom: 2px solid #34d058;
      padding-bottom: 5px;
    }
    #menuLateral button {
      background: #34d058;
      border: none;
      color: #121917;
      padding: 10px;
      border-radius: 25px;
      font-weight: 700;
      cursor: pointer;
      box-shadow: 0 0 10px #34d058cc;
      transition: background-color 0.3s ease;
    }
    #menuLateral button:hover {
      background: #2fb44d;
      box-shadow: 0 0 18px #34d058ff;
    }
    #menuLateral .fecharMenu {
      background: transparent;
      color: #d1f2a5;
      font-size: 1.4rem;
      font-weight: 900;
      align-self: flex-end;
      cursor: pointer;
      border: none;
      padding: 0 5px;
    }
    #menuLateral label, #menuLateral select, #menuLateral input {
      font-weight: 700;
      background-color: #18241a;
      color: #d1f2a5;
      border: none;
      border-radius: 8px;
      padding: 8px;
      width: 100%;
      box-sizing: border-box;
      margin-top: 5px;
    }
    #menuLateral input[type="text"] {
      font-weight: normal;
    }

    /* Lista de carros */
    main {
      flex-grow: 1;
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 20px;
      padding: 15px 20px 30px;
      max-width: 1200px;
      margin: 0 auto;
      width: 100%;
      box-sizing: border-box;
    }
    .car-card {
      background: #1b2a1f;
      width: 100%;
      aspect-ratio: 1 / 1;
      padding: 15px;
      border-radius: 20px;
      box-shadow:
        0 4px 10px rgba(52, 208, 88, 0.3),
        inset 0 0 15px #2d7e1a66;
      text-align: center;
      display: flex;
      flex-direction: column;
      justify-content: start;
      color: #d1f2a5;
      transition: transform 0.3s ease, box-shadow 0.3s ease;
      cursor: default;
      user-select: none;
      position: relative;
      overflow: hidden;
    }
    .car-card:hover {
      transform: translateY(-8px);
      box-shadow:
        0 10px 25px rgba(52, 208, 88, 0.7),
        inset 0 0 20px #3fba2baa;
    }
    .car-card img {
      width: 100%;
      height: auto;
      max-height: 50%;
      object-fit: cover;
      border-radius: 15px;
      margin-bottom: 15px;
      filter: drop-shadow(0 0 8px #34d058);
      user-select: none;
      flex-shrink: 0;
      transition: transform 0.3s ease;
    }
    .car-card:hover img {
      transform: scale(1.05);
    }
    .car-card h3 {
      margin: 0 0 8px;
      font-size: 1.4rem;
      font-weight: 700;
      text-shadow: 0 0 8px #34d058cc;
      user-select: text;
      flex-grow: 1;
    }
    .car-card p {
      margin: 0;
      font-weight: 600;
      color: #9fca7c;
      text-shadow: 0 0 5px #2a5c2e;
      cursor: pointer;
      user-select: text;
      transition: color 0.3s ease;
    }
    .car-card p:hover {
      color: #34d058;
    }

    /* Botão remover */
    .btnRemover {
      position: absolute;
      top: 10px;
      right: 10px;
      background: #e84545;
      border: none;
      color: white;
      border-radius: 50%;
      width: 28px;
      height: 28px;
      font-weight: 700;
      cursor: pointer;
      opacity: 0.85;
      transition: opacity 0.3s ease;
      user-select: none;
    }
    .btnRemover:hover {
      opacity: 1;
      background: #ff5555;
    }

    /* Área adicionar carro */
    #areaAdicionarCarro {
      display: none;
      margin: 10px 20px 20px;
      max-width: 1200px;
      width: 100%;
      box-sizing: border-box;
      display: flex;
      gap: 10px;
      flex-wrap: wrap;
      align-items: center;
      justify-content: center;
      background: #18241a;
      padding: 15px 20px;
      border-radius: 20px;
      box-shadow: 0 0 12px #34d058aa inset;
    }
    #areaAdicionarCarro select,
    #areaAdicionarCarro input[type="text"],
    #areaAdicionarCarro input[type="file"],
    #areaAdicionarCarro button {
      font-weight: 700;
      background-color: #1f2a20;
      color: #d1f2a5;
      border: none;
      border-radius: 25px;
      padding: 10px 15px;
      cursor: pointer;
      box-shadow: inset 0 0 8px #34d058;
      transition: background-color 0.3s ease, box-shadow 0.3s ease;
    }
    #areaAdicionarCarro input[type="text"],
    #areaAdicionarCarro select {
      flex-grow: 1;
      max-width: 200px;
    }
    #areaAdicionarCarro input[type="file"] {
      flex-grow: 1;
      max-width: 180px;
      cursor: pointer;
    }
    #areaAdicionarCarro button:hover {
      background-color: #2fb44d;
      box-shadow: 0 0 18px #34d058ff;
    }

    /* Scrollbar */
    ::-webkit-scrollbar {
      width: 8px;
      height: 8px;
    }
    ::-webkit-scrollbar-track {
      background: #121917;
    }
    ::-webkit-scrollbar-thumb {
      background-color: #34d058;
      border-radius: 20px;
      border: 2px solid #121917;
    }
  </style>
</head>
<body>

<header>
  <img src="https://cdn.discordapp.com/attachments/1395776398869790850/1404427449470685254/dbd1dd651d70777c7c91d9051d8856ca-removebg-preview.png?ex=689b267c&is=6899d4fc&hm=804bdf797d62dbcae7e8f5df5897c670a697fae276b23fac66bc727aaee85310&" alt="Logo" />
  <div class="site-name" id="siteName">Just Vehicles</div>
  <input
    type="text"
    class="search-bar"
    placeholder="Pesquisar carro..."
    oninput="filtrarCarros()"
    aria-label="Pesquisar carro"
  />
</header>

<!-- Botão 3 pontinhos fixo para abrir menu -->
<button id="btnConfig" aria-label="Abrir configurações" title="Configurações" style="display:none;">
  <span></span>
  <span></span>
  <span></span>
</button>

<!-- Menu lateral -->
<aside id="menuLateral" role="menu" aria-label="Menu de configurações administrativas">
  <button class="fecharMenu" aria-label="Fechar menu">&times;</button>
  <h2>Configurações</h2>

  <label for="selectCargo" style="font-weight: 700;">Selecione o cargo do usuário atual:</label>
  <select id="selectCargo" aria-label="Selecionar cargo do usuário atual" style="padding: 8px; border-radius: 8px; border: none; background-color: #18241a; color: #d1f2a5;">
    <option value="ceo">Ceo (total)</option>
    <option value="adm">Administrador (adm)</option>
    <option value="randola">Usuário comum (randola)</option>
  </select>

  <button id="btnCopiarLista" aria-label="Copiar lista de nomes">Copiar lista de nomes</button>

  <hr style="border-color:#34d05855; margin: 15px 0;" />

  <h2>Alterar permissão de usuário</h2>
  <label for="usuarioNome">Nome do usuário:</label>
  <input type="text" id="usuarioNome" placeholder="Digite o nome do usuário" aria-label="Nome do usuário" />

  <label for="novaPermissao">Nova permissão:</label>
  <select id="novaPermissao" aria-label="Nova permissão do usuário">
    <option value="ceo">Ceo (total)</option>
    <option value="adm">Administrador (adm)</option>
    <option value="randola">Usuário comum (randola)</option>
  </select>

  <button id="btnAtualizarPermissao" aria-label="Atualizar permissão">Atualizar Permissão</button>
</aside>

<div id="areaAdicionarCarro" role="region" aria-label="Filtros e adicionar carro">
  <select id="categoriaFiltro" onchange="filtrarCarros()" aria-label="Filtrar por categoria">
    <option value="">Todas Categorias</option>
    <option value="SUV">SUV</option>
    <option value="Sedan">Sedan</option>
    <option value="Esportivo">Esportivo</option>
    <option value="Pickup">Pickup</option>
  </select>

  <input type="text" id="novoNome" placeholder="Nome do carro" aria-label="Nome do carro" />
  <select id="novaCategoria" aria-label="Categoria do carro">
    <option value="SUV">SUV</option>
    <option value="Sedan">Sedan</option>
    <option value="Esportivo">Esportivo</option>
    <option value="Pickup">Pickup</option>
  </select>
  <input type="file" id="novaImagem" accept="image/*" aria-label="Imagem do carro" />
  <button onclick="adicionarCarro()" aria-label="Adicionar carro">Adicionar Carro</button>
</div>

<main id="listaCarros" aria-live="polite" aria-relevant="additions removals">
  <!-- Carros iniciais -->
  <div class="car-card" data-nome="BMW X6" data-categoria="SUV">
    <img src="https://source.unsplash.com/200x150/?bmw" alt="BMW X6" />
    <h3>BMW X6</h3>
    <p title="Clique para copiar o nome do veículo">SUV</p>
  </div>
  <div class="car-card" data-nome="Ferrari F8" data-categoria="Esportivo">
    <img src="https://source.unsplash.com/200x150/?ferrari" alt="Ferrari F8" />
    <h3>Ferrari F8</h3>
    <p title="Clique para copiar o nome do veículo">Esportivo</p>
  </div>
  <div class="car-card" data-nome="Toyota Hilux" data-categoria="Pickup">
    <img src="https://source.unsplash.com/200x150/?pickup" alt="Toyota Hilux" />
    <h3>Toyota Hilux</h3>
    <p title="Clique para copiar o nome do veículo">Pickup</p>
  </div>
</main>

<script>
  // Usuário atual e permissão (inicial)
  let usuarioAtual = {
    nome: "MonarckDev",
    permissao: "ceo" // pode ser 'ceo', 'adm', 'randola'
  };

  const btnConfig = document.getElementById("btnConfig");
  const menuLateral = document.getElementById("menuLateral");
  const areaAdicionar = document.getElementById("areaAdicionarCarro");
  const selectCargo = document.getElementById("selectCargo");
  const listaCarros = document.getElementById("listaCarros");

  // Inputs para alterar permissão
  const usuarioNomeInput = document.getElementById("usuarioNome");
  const novaPermissaoSelect = document.getElementById("novaPermissao");
  const btnAtualizarPermissao = document.getElementById("btnAtualizarPermissao");

  // Atualiza interface baseado na permissão
  function atualizarInterface() {
    if (usuarioAtual.permissao === "ceo") {
      btnConfig.style.display = "flex";
      areaAdicionar.style.display = "flex";
      mostrarBotoesRemover(true);
    } else if (usuarioAtual.permissao === "adm") {
      btnConfig.style.display = "flex";
      areaAdicionar.style.display = "flex";
      mostrarBotoesRemover(true);
    } else if (usuarioAtual.permissao === "randola") {
      btnConfig.style.display = "none";
      areaAdicionar.style.display = "none";
      mostrarBotoesRemover(false);
    }

    // Atualiza o select no menu lateral para refletir o usuário atual
    selectCargo.value = usuarioAtual.permissao;
  }

  // Mostra ou esconde os botões remover nos cards
  function mostrarBotoesRemover(mostrar) {
    if (mostrar) {
      // Adiciona botão remover em todos os carros que ainda não tem
      listaCarros.querySelectorAll(".car-card").forEach(card => {
        if (!card.querySelector(".btnRemover")) {
          const btn = document.createElement("button");
          btn.className = "btnRemover";
          btn.title = "Remover carro";
          btn.textContent = "×";
          btn.addEventListener("click", () => {
            if(confirm(`Remover o carro "${card.dataset.nome}"?`)) {
              card.remove();
            }
          });
          card.appendChild(btn);
        }
      });
    } else {
      // Remove todos os botões remover
      listaCarros.querySelectorAll(".btnRemover").forEach(btn => btn.remove());
    }
  }

  // Inicializa interface e select
  function init() {
    selectCargo.value = usuarioAtual.permissao;
    atualizarInterface();
  }
  init();

  // Troca o cargo ao mudar no select do menu lateral
  selectCargo.addEventListener("change", () => {
    usuarioAtual.permissao = selectCargo.value;
    atualizarInterface();
    menuLateral.classList.remove("ativo");
  });

  // Abrir e fechar menu lateral
  btnConfig.addEventListener("click", () => {
    menuLateral.classList.toggle("ativo");
  });
  menuLateral.querySelector(".fecharMenu").addEventListener("click", () => {
    menuLateral.classList.remove("ativo");
  });

  // Copiar lista de nomes no menu lateral (adm e ceo)
  document.getElementById("btnCopiarLista").addEventListener("click", () => {
    if (usuarioAtual.permissao === "randola") {
      alert("Você não tem permissão para esta ação.");
      return;
    }
    const carros = document.querySelectorAll(".car-card");
    let nomes = [];
    carros.forEach(carro => {
      nomes.push(carro.dataset.nome);
    });
    const texto = nomes.join("\n");
    navigator.clipboard.writeText(texto).then(() => {
      alert("Lista de nomes copiada para área de transferência!");
    }).catch(() => {
      alert("Erro ao copiar lista.");
    });
  });

  // Filtrar carros pela busca e categoria
  function filtrarCarros() {
    const busca = document.querySelector(".search-bar").value.toLowerCase();
    const categoria = document.getElementById("categoriaFiltro")?.value || "";
    const carros = document.querySelectorAll(".car-card");

    carros.forEach(carro => {
      const nome = carro.dataset.nome.toLowerCase();
      const cat = carro.dataset.categoria;

      if ((nome.includes(busca) || busca === "") &&
          (categoria === "" || cat === categoria)) {
        carro.style.display = "flex";
      } else {
        carro.style.display = "none";
      }
    });
  }

  // Copiar nome do veículo ao clicar na categoria (texto <p>) - somente adm e ceo podem copiar
  listaCarros.addEventListener("click", function(e) {
    if (e.target.tagName.toLowerCase() === "p" && e.target.parentElement.classList.contains("car-card")) {
      if(usuarioAtual.permissao === "adm" || usuarioAtual.permissao === "ceo") {
        const nomeVeiculo = e.target.parentElement.dataset.nome;
        navigator.clipboard.writeText(nomeVeiculo).then(() => {
          alert(`Nome do veículo "${nomeVeiculo}" copiado para a área de transferência!`);
        }).catch(() => {
          alert("Erro ao copiar o nome do veículo.");
        });
      }
    }
  });

  // Função para adicionar carro (disponível para adm e ceo)
  function adicionarCarro() {
    if(usuarioAtual.permissao !== "adm" && usuarioAtual.permissao !== "ceo") {
      alert("Você não tem permissão para adicionar carros.");
      return;
    }

    const nomeInput = document.getElementById("novoNome");
    const categoriaInput = document.getElementById("novaCategoria");
    const imagemInput = document.getElementById("novaImagem");

    const nome = nomeInput.value.trim();
    const categoria = categoriaInput.value;
    const arquivoImagem = imagemInput.files[0];

    if (!nome) {
      alert("Por favor, informe o nome do carro.");
      return;
    }
    if (!categoria) {
      alert("Por favor, selecione a categoria do carro.");
      return;
    }
    if (!arquivoImagem) {
      alert("Por favor, selecione uma imagem para o carro.");
      return;
    }

    const leitor = new FileReader();
    leitor.onload = function(event) {
      const urlImagem = event.target.result;

      // Criar novo card
      const novoCard = document.createElement("div");
      novoCard.className = "car-card";
      novoCard.dataset.nome = nome;
      novoCard.dataset.categoria = categoria;

      novoCard.innerHTML = `
        <img src="${urlImagem}" alt="${nome}" />
        <h3>${nome}</h3>
        <p title="Clique para copiar o nome do veículo">${categoria}</p>
      `;

      // Se tiver permissão para remover, adiciona o botão remover
      if (usuarioAtual.permissao === "adm" || usuarioAtual.permissao === "ceo") {
        const btnRemover = document.createElement("button");
        btnRemover.className = "btnRemover";
        btnRemover.title = "Remover carro";
        btnRemover.textContent = "×";
        btnRemover.addEventListener("click", () => {
          if (confirm(`Remover o carro "${nome}"?`)) {
            novoCard.remove();
          }
        });
        novoCard.appendChild(btnRemover);
      }

      listaCarros.appendChild(novoCard);

      // Limpar inputs
      nomeInput.value = "";
      categoriaInput.value = "";
      imagemInput.value = "";

      alert(`Carro "${nome}" adicionado com sucesso!`);
      filtrarCarros();
    };

    leitor.readAsDataURL(arquivoImagem);
  }

  // Atualizar permissão do usuário (simulação simples)
  btnAtualizarPermissao.addEventListener("click", () => {
    const nomeUsuario = usuarioNomeInput.value.trim();
    const novaPermissao = novaPermissaoSelect.value;

    if (!nomeUsuario) {
      alert("Por favor, digite o nome do usuário.");
      return;
    }

    // Simulação: só permite alterar permissão do usuário atual
    if (nomeUsuario.toLowerCase() === usuarioAtual.nome.toLowerCase()) {
      usuarioAtual.permissao = novaPermissao;
      atualizarInterface();
      alert(`Permissão do usuário "${nomeUsuario}" atualizada para "${novaPermissao}".`);
    } else {
      alert(`Usuário "${nomeUsuario}" não encontrado (simulação).`);
    }
  });
</script>

</body>
</html>
