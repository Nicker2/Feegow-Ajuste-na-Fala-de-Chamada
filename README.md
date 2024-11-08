# Feegow - Ajuste na Fala de Chamada

## Descrição

Este é um script do Tampermonkey para modificar a fala gerada pelo sistema Feegow utilizado no **HOC Hospital de Olhos de Caraguatatuba**, especificamente na parte da chamada de pacientes para atendimento. O script intercepta a função de síntese de fala do navegador e altera o texto de chamadas de pacientes para a sala de exames 01, substituindo a referência a um doutor (que não está presente) por uma referência à enfermagem.

### Funcionalidade

O script é projetado para detectar chamadas de pacientes com a frase "dr. está chamando paciente [nome]" seguida da referência à sala de exames 01. Quando detectado, o script altera a fala, substituindo "dr." por "Enfermagem", garantindo que a informação transmitida seja precisa, já que o doutor não está presente durante o atendimento.

Além disso, o script também ajusta a fala quando o texto contém apenas a referência à sala de exame 01, alterando a frase para que mencione diretamente a enfermagem chamando o paciente.

### Como funciona

1. **Interceptação da função de fala**: A função `speechSynthesis.speak` do navegador é interceptada, permitindo que o script altere o texto antes que ele seja falado.
   
2. **Verificação de condições**: O script verifica se o texto da fala contém a frase "exame 01" ou "dr. está chamando paciente [nome]". Dependendo da condição encontrada, o texto será modificado.

3. **Modificação do texto**:
   - Se a fala mencionar "dr. está chamando paciente [nome] para atendimento na sala de exame 01 - matriz", o nome do paciente é extraído e substitui-se "dr." por "Enfermagem".
   - Se a fala contiver apenas "exame 01", a frase é substituída para "Enfermagem está chamando para atendimento na sala de exame 01".
   
4. **Execução da fala modificada**: Após as modificações, o texto é passado de volta para a função original de síntese de fala para ser pronunciado pelo navegador.

### Como usar

1. Instale o Tampermonkey na sua extensão do navegador.
2. Crie um novo script no Tampermonkey e cole o código acima.
3. O script funcionará automaticamente quando você acessar a URL do sistema Feegow: `https://core.feegow.com/tvcall/panelV3/vvAM/*`.

### Exemplo de Modificação de Fala

#### Texto original:
> "Dr. está chamando paciente Rafaela para atendimento na sala de exame 01 - matriz"

#### Texto modificado:
> "Enfermagem está chamando paciente Rafaela para atendimento na sala de exame 01"

### Logs de Depuração

O script inclui diversos logs de depuração no console para auxiliar no monitoramento de sua execução. Isso pode ser útil para verificar se as condições estão sendo atendidas corretamente e se o texto está sendo modificado conforme esperado.

### Dependências

- **Tampermonkey**: Extensão do navegador para rodar scripts de usuários (userscripts).
- **Navegador compatível**: O script foi testado em navegadores como Google Chrome e Firefox, que suportam a API `speechSynthesis`.

### Atenção

- Este script foi desenvolvido especificamente para o sistema Feegow do HOC Hospital de Olhos de Caraguatatuba.
- Pode ser necessário ajustar a lógica caso haja outras modificações nas mensagens de fala ou no formato dos dados.

---

### Licença

Este projeto está licenciado sob a Licença MIT - veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---

### Créditos

Autor: **Nicolas Bonza Cavalari Borges** (você)

---
