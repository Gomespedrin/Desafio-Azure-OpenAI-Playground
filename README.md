Resumo do que aprendi sobre desenvolvimento de aplicações com Azure OpenAI e Semantic Kernel

Chamada de API no Azure OpenAI:

É possível interagir com os modelos do Azure OpenAI via chamadas REST.

Precisamos de credenciais (chaves e endpoint do Azure) para autenticar as requisições.

Parâmetros de configuração como temperatura, max_tokens, top_p, entre outros, podem ser enviados via JSON para controlar a resposta.

Exemplo de chamada (pseudo-curl):

bash
Copiar
Editar
curl https://{seu-endpoint}.openai.azure.com/openai/deployments/{nome-do-modelo}/chat/completions?api-version=2023-03-15-preview \
-H "Content-Type: application/json" \
-H "api-key: {sua-chave}" \
-d '{
  "messages": [{"role": "user", "content": "Olá, tudo bem?"}],
  "max_tokens": 100,
  "temperature": 0.7
}'
Configurações importantes:

Deployments: Cada modelo (por exemplo, GPT-3.5, GPT-4, etc.) precisa ser implantado no Portal Azure para receber um “deployment name”.

API Versions: É importante utilizar a versão correta da API (exemplo: ?api-version=2023-03-15-preview).

Segurança: Armazenar a chave de API de forma segura e não expor diretamente em repositórios públicos.

Integração com o Semantic Kernel:

O Semantic Kernel é uma estrutura (principalmente para .NET, mas também há suporte para outras linguagens) que facilita a orquestração entre prompts, memórias e modelos de linguagem.

Permite criar “Skills” (funções) para lidar com tarefas como sumarização, geração de texto e até integração com sistemas externos.

É possível configurar o Kernel para usar o Azure OpenAI fornecendo os parâmetros de conexão (endpoint, chave, nome do modelo) e depois chamar métodos de geração de texto ou chat diretamente na aplicação.

Aplicações práticas:

Chatbots: Conexão com Azure OpenAI usando REST ou uma biblioteca do Azure para criar um chatbot personalizado.

Automação de processos: Utilizar chamadas de API em pipelines de dados e fluxos de trabalho, recebendo texto gerado ou comandos interpretados pelo LLM.

Orquestração com Semantic Kernel: Facilita a construção de soluções mais complexas (por exemplo, extrair informações de textos, criar resumos e armazenar resultados), organizando tudo em “skills” modulares.
