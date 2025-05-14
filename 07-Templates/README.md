
---

#  Pasta 07-Templates

Esta pasta armazena **modelos reutilizáveis de notas** (templates) para os diferentes tipos de anotações mantidas no Vault.  
Os arquivos daqui são usados em conjunto com o plugin **Templater** ou manualmente copiados ao iniciar uma nova nota.

A ideia é manter uma estrutura padrão para notas de leitura, aula, projeto, reunião, log de pesquisa, entre outros — garantindo clareza, uniformidade e economia de tempo.

---

##  Exemplos de templates existentes

| Arquivo                        | Uso recomendado |
|-------------------------------|-----------------|
| `template-leitura.md`         | Fichamento de artigos e livros |
| `template-aula.md`            | Anotações de aulas presenciais ou online |
| `template-log-pesquisa.md`    | Registro de sessões de trabalho, experimentos ou análise |
| `template-reuniao.md`         | Registro de reuniões com orientadores, coautores ou grupos |
| `template-disciplina.md`      | Organização geral de uma disciplina cursada |
| `template-projeto.md`         | Estrutura de nota para um projeto de pesquisa ou pessoal |
| `template-codigo.md`          | Explicação e documentação de trechos de código ou funções |
| `template-inbox.md`           | Anotação rápida a ser processada depois |
| `template-formulario-matematico.md` | Registro organizado de fórmulas, identidades e propriedades |

---

##  Como usar com o plugin Templater

1. Instale e ative o plugin **Templater** via *Community Plugins*
2. Vá em `Settings → Templater`
3. Configure o campo **Template folder location** com:

```

07-Templates

```

4. Agora você pode:
   - Inserir templates com `Ctrl + P → Templater: Insert template`
   - Criar novos comandos personalizados
   - Usar variáveis dinâmicas como `{{date}}`, `{{title}}`, `{{tp.file.title}}`, etc.

---

##  Boas práticas

- Mantenha nomes de arquivo descritivos e sem espaços
- Comece cada template com um título claro (usando `#`)
- Inclua campos preenchíveis (como `{{autor}}`, `{{ano}}`, `{{tema}}`)
- Atualize os templates à medida que suas preferências evoluírem

---

##  Sugestões de expansão futura

- Templates para: finanças pessoais, organização semanal, tarefas pendentes
- Templates didáticos: resolução de listas, planejamento de aula
- Modelos para documentação de código mais técnica (docstring style)



---