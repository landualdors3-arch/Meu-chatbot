<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <title>Assistente Virtual Landualdo</title>
  <style>
    body { font-family: Arial, sans-serif; background: #f4f4f4; margin: 0; }
    .chat-container { max-width: 400px; margin: 40px auto; background: #fff; border-radius: 8px; box-shadow: 0 2px 8px #0002; padding: 20px; }
    .chat-box { height: 320px; overflow-y: auto; border: 1px solid #ddd; border-radius: 6px; padding: 10px; background: #fafafa; margin-bottom: 10px;}
    .user { text-align: right; color: #1976d2; margin-bottom: 6px;}
    .bot { text-align: left; color: #333; margin-bottom: 6px;}
    .input-row { display: flex; }
    input[type="text"] { flex: 1; padding: 8px; border-radius: 4px; border: 1px solid #ccc;}
    button { padding: 8px 16px; border-radius: 4px; border: none; background: #1976d2; color: #fff; margin-left: 6px;}
    button:hover { background: #125ea7;}
    h2 { text-align:center; color:#1976d2;}
  </style>
</head>
<body>
  <div class="chat-container">
    <h2>Assistente Landualdo</h2>
    <div class="chat-box" id="chatBox">
      <div class="bot">Olá! Sou o assistente virtual do Landualdo Rodrigues. Pergunte sobre experiência, formação, cursos, objetivos ou salário!</div>
    </div>
    <form id="chatForm" class="input-row" autocomplete="off">
      <input type="text" id="userInput" placeholder="Digite sua pergunta..." required autofocus>
      <button type="submit">Enviar</button>
    </form>
  </div>

<script>
// --- Banco de Dados Completo ---
const knowledgeBase = {
  nome: "Landualdo Rodrigues Souza",
  idade: "35 anos (nascido em 03/11/1990)",
  endereco: "Contagem, MG (Bairro Flamengo). Originalmente de Salvador, BA, mora em Minas Gerais há 15 anos.",
  familia: "Tem uma filha de 6 anos que mora em Betim, MG.",
  contato: "Telefone/Whatsapp: (31) 97202-2291, E-mail: landualdo.rs4@gmail.com.",
  portfolio: "Portfólio Power BI: https://sites.google.com/view/portfolio-landualdo/in%C3%ADcio",
  formacao: `Graduação em <b>Gestão da Qualidade</b> e cursando <b>MBA em Gestão da Qualidade</b>. Sólida base em Sistemas de Gestão da Qualidade (SGQ), auditorias internas, análise de indicadores e melhoria contínua de processos.`,
  cursos: `Certificações e cursos:<br>- <b>Analista da Qualidade</b><br>- <b>Auditor Interno SGI</b> (ISO 9001, 14001, 45001, 19011)<br>- <b>Excel Avançado e Power BI</b><br>- <b>Gestão de Indicadores de Qualidade e Produtividade</b><br>- <b>Ferramentas da Qualidade:</b> 5W2H, Ishikawa, MASP, 8D, Histograma, Pareto, Fluxograma<br>- <b>Filosofias:</b> Kaizen, WCM<br>- <b>Segurança:</b> NR 1 (Riscos Ocupacionais), NR 6 (EPI), LEPAR`,
  experiencia_atual: `Atualmente é <b>Analista da Qualidade e Processos na Açocon</b> (desde Abril/2025). Atua com controle de qualidade, padronização de processos, gestão documental, elaboração de indicadores/dashboards em Excel, revisão de procedimentos e treinamentos internos.`,
  experiencia_aethra: `Na <b>AETHRA SISTEMAS AUTOMOTIVOS S.A.</b> (Fev/2023 – Abr/2025) atuou como:<br>1. Técnico de Ensaio e Fadiga JR<br>2. Técnico de Laboratório Metalográfico<br>3. Estagiário em Gestão da Qualidade<br>Desenvolveu competências em auditoria, metrologia, ensaios mecânicos e relatórios técnicos no setor automotivo.`,
  experiencia_outras: `Também trabalhou na <b>DIBS LTDA</b> (Serviços Fotográficos/Design Gráfico) e na <b>MASTER FOTO</b> (Comunicação Visual), desenvolvendo organização, controle de fluxo e atenção à qualidade.`,
  experiencia_total: "Mais de <b>10 anos e 9 meses de experiência profissional</b>, sendo <b>2 anos e 9 meses</b> dedicados à gestão da qualidade e processos industriais.",
  objetivos: `Consolidar-se como especialista em Gestão da Qualidade e Processos, evoluindo para cargos de supervisão ou coordenação. Busca implementar sistemas de indicadores, atuar com melhoria contínua (Lean, PDCA, Kaizen), contribuir com auditorias internas/externas e treinamento de equipes.`,
  habilidades: `<b>Especialista em:</b><br>- Ferramentas da Qualidade: PDCA, Ishikawa, 5 Porquês, Pareto, FMEA, MASP, 8D<br>- Normas: ISO 9001:2025, 14001, 45001, IATF 16949<br>- Análise de Dados: Excel Avançado (dashboards), Power BI<br>- Processos: Criação/revisão de instruções técnicas, fluxogramas<br>- Auditoria interna e controle metrológico`,
  salario: `A questão salarial é tratada em etapas avançadas do processo seletivo. Landualdo busca remuneração compatível com sua experiência (nível Analista Pleno/Sênior) e formação (MBA em Gestão da Qualidade). Está aberto a propostas que reflitam seu valor e potencial para contribuir com resultados e melhoria contínua.`,
  disponibilidade: `Total disponibilidade para qualquer horário e aberto a horas extras.`,
  lazer: `Gosta de jogar, estudar (atualização profissional), praticar esportes (capoeira) e cinema.`,
  resumo: `Landualdo Rodrigues Souza é Analista da Qualidade e Processos com mais de 10 anos de experiência profissional (2 anos e 9 meses em qualidade industrial), graduação/MBA em Gestão da Qualidade. Especialista em normas ISO, ferramentas da qualidade e análise de dados. Foco em melhoria contínua, auditorias e otimização de processos.`
};

const keywordMap = [
 { keywords: ["idade", "quantos anos", "nascimento"], key: "idade" },
 { keywords: ["nome", "quem é", "quem e", "resumo"], key: "resumo" },
 { keywords: ["contato", "telefone", "email", "whatsapp"], key: "contato" },
 { keywords: ["formacao", "formação", "estudos", "mba", "graduação", "academica"], key: "formacao" },
 { keywords: ["curso", "cursos", "certificação", "certificações", "auditor", "iso", "excel", "power bi"], key: "cursos" },
 { keywords: ["experiencia", "experiência", "trabalho", "carreira", "empregos", "historico"], key: "experiencia_total" },
 { keywords: ["aethra"], key: "experiencia_aethra" },
 { keywords: ["acocon", "atual"], key: "experiencia_atual" },
 { keywords: ["habilidades", "ferramentas"], key: "habilidades" },
 { keywords: ["familia", "filha", "pessoal"], key: "familia" },
 { keywords: ["endereco", "endereço", "mora", "onde", "residencia"], key: "endereco" },
 { keywords: ["portfolio", "projetos"], key: "portfolio" },
 { keywords: ["objetivo", "objetivos", "meta", "futuro"], key: "objetivos" },
 { keywords: ["salario", "pretensão", "remuneração", "valor"], key: "salario" },
 { keywords: ["disponibilidade", "horario", "extra"], key: "disponibilidade" },
 { keywords: ["lazer", "hobby", "jogar", "esporte", "cinema"], key: "lazer" }
];

async function getBotResponse(userMessage) {
 const normalized = userMessage.toLowerCase().normalize("NFD").replace(/[\u0300-\u036f]/g,"");
 let response = knowledgeBase.resumo;
 for(const item of keywordMap){
   if(item.keywords.some(k => normalized.includes(k))){
     if(item.key === 'experiencia_total'){
       response = `Experiência total: ${knowledgeBase.experiencia_total}<br><strong>Atual:</strong> ${knowledgeBase.experiencia_atual}<br><strong>AETHRA:</strong> ${knowledgeBase.experiencia_aethra}<br><strong>Outras experiências:</strong> ${knowledgeBase.experiencia_outras}`;
     } else {
       response = knowledgeBase[item.key];
     }
     break;
   }
 }
 if(/(ola|oi|bom dia|boa tarde|boa noite)/.test(normalized)){
   response = `Olá! Sou o assistente virtual do Landualdo Rodrigues. Pergunte sobre experiência, formação, cursos, objetivos ou salário!`;
 }
 if(response === knowledgeBase.resumo && !normalized.includes("resumo")){
   response = `Desculpe, não encontrei uma resposta específica para essa pergunta.<br>Aqui está um resumo do Landualdo:<br>${knowledgeBase.resumo}<br>Tente perguntar sobre cursos, ferramentas, salário ou experiência atual para obter detalhes.`;
 }
 await new Promise(r => setTimeout(r,600));
 return response;
}

// --- Chatbot Frontend ---
const chatBox = document.getElementById('chatBox');
const chatForm = document.getElementById('chatForm');
const userInput = document.getElementById('userInput');

function addMessage(text, sender) {
 const div = document.createElement('div');
 div.className = sender;
 div.innerHTML = text;
 chatBox.appendChild(div);
 chatBox.scrollTop = chatBox.scrollHeight;
}

chatForm.addEventListener('submit', async function(e){
 e.preventDefault();
 const msg = userInput.value.trim();
 if(!msg) return;
 addMessage(msg,'user');
 userInput.value = '';
 const botReply = await getBotResponse(msg);
 addMessage(botReply,'bot');
});
</script>
</body>
</html>
