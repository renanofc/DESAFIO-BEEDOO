# Desafio Beedoo

## User Story

### Título:
Como usuário, quero poder listar, criar e excluir cursos na plataforma Beedoo para gerenciar minhas atividades de ensino.

### Critérios de Aceitação:
1. O usuário deve poder visualizar a lista de cursos cadastrados.
2. O usuário deve poder criar um novo curso fornecendo todas as informações obrigatórias.
3. O usuário deve poder excluir um curso da lista.

## Decisões Tomadas
A análise foi feita com base na página do website informado. Identifiquei as principais funcionalidades que precisam ser testadas: a listagem de cursos, a criação de novos cursos e a exclusão de cursos existentes.

## Cenários de Teste

### Feature: Gerenciamento de Cursos

#### Scenario: Visualizar lista de cursos cadastrados
Given o usuário está na página de lista de cursos
When a página é carregada
Then a lista de cursos cadastrados deve ser exibida

#### Scenario: Criar um curso com sucesso
Given o usuário está na página de cadastro de curso
When o usuário preenche todos os campos obrigatórios
And o usuário clica em "Cadastrar Curso"
Then o curso deve ser criado com sucesso e exibido na lista de cursos

#### Scenario: Tentar criar um curso sem preencher campos obrigatórios
Given o usuário está na página de cadastro de curso
When o usuário não preenche os campos obrigatórios
And o usuário clica em "Cadastrar Curso"
Then o curso não deve ser criado e uma mensagem de erro deve ser exibida

#### Scenario: Excluir um curso com sucesso

Given o usuário está na página de lista de cursos
And um curso está disponível na lista
When o usuário clica em "Excluir Curso" para um curso
Then o curso deve ser removido da lista de cursos



# Relatório de Bugs
## Bug 1: Erro ao tentar excluir um curso
### Descrição: Ao tentar excluir um curso, a página exibe a mensagem "Curso excluído com sucesso", porém o curso não é removido da lista de cursos. No console de rede (network), é exibido um erro 405 Method Not Allowed.

#### Passos para Reproduzir:

Navegue até a página de lista de cursos.
Clique em "Excluir Curso" para qualquer curso disponível.
Observe que a página exibe a mensagem "Curso excluído com sucesso", mas o curso permanece na lista.
Verifique o console de rede (network) para ver o erro 405 Method Not Allowed.

## Gravidade: Alta

Resultados Esperados: O curso deve ser removido da lista de cursos e a mensagem "Curso excluído com sucesso" deve ser exibida corretamente.

Resultados Atuais: A mensagem "Curso excluído com sucesso" é exibida, mas o curso não é removido da lista e um erro 405 Method Not Allowed é retornado.

## Possíveis Causas:

O método DELETE não está permitido ou não está configurado corretamente no servidor.
Problemas de configuração de rota no backend.
Restrições de CORS (Cross-Origin Resource Sharing) que estão impedindo a requisição DELETE.

## Evidências:

Request URL: https://creative-sherbet-a51eac.netlify.app/test-api/courses/1
Request Method: DELETE
Status Code: 405 Method Not Allowed
Remote Address: 52.67.97.86:443
Referrer Policy: strict-origin-when-cross-origin


## Bug 2: Criação de curso com campos obrigatórios em branco
### Descrição: Ao tentar criar um curso sem preencher os campos obrigatórios, o curso é criado com campos em branco, sem exibir qualquer mensagem de erro.

#### Passos para Reproduzir:

Navegue até a página de cadastro de curso.
Deixe todos os campos obrigatórios em branco.
Clique em "Cadastrar Curso".
Observe que o curso é criado com campos em branco e aparece na lista de cursos.

## Gravidade: Alta

Resultados Esperados: A criação do curso deve ser impedida e uma mensagem de erro deve ser exibida informando que os campos obrigatórios precisam ser preenchidos.
Resultados Atuais: O curso é criado com campos em branco sem exibir mensagem de erro.

## Possíveis Causas:

Falta de validação de campos obrigatórios no frontend e/ou backend.

## Evidências:
Ao verificar a lista de cursos, um curso com campos em branco é exibido após a tentativa de criação com campos não preenchidos.



# Segue abaixo os links para as evidências de teste (MP4) e link para planilha de casos de testes.

Evidências de testes: https://drive.google.com/drive/folders/1fqyFoB2IIIdXV3D7K_7p3CCA5jzf1iD_?usp=sharing


Planilha de casos de testes: https://docs.google.com/spreadsheets/d/1TlCGgM1H68sVXKXWS-zDZMiwqsBwdPe_SZtBqWG3_20/edit?usp=sharing
