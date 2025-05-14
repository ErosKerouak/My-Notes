
---

#  Pasta 06-Referências

Esta pasta armazena **notas bibliográficas baseadas em fontes formais**, como artigos científicos, livros, teses, relatórios e capítulos.  
Aqui ficam os registros estruturados das referências que sustentam projetos, leituras e experimentos ao longo do Vault.

Ela se integra ao plugin **Citations** e ao arquivo `referencias.bib`, permitindo o uso de citações automáticas, geração de notas com metadados e conexões diretas entre conteúdo e fontes.

---

##  Quando usar esta pasta

- Ao gerar uma **nota de leitura automática** com o plugin Citations
- Ao registrar manualmente uma referência importante com base em seu BibTeX
- Para guardar **resumos, citações úteis e comentários críticos** de uma fonte específica
- Para centralizar o conhecimento de base formal reutilizável em diferentes projetos

---

##  Nome e estrutura das notas

As notas são geralmente nomeadas pelo `citekey` (ex: `blakely1995`, `cordell1985`, `hofmann2005`) e geradas automaticamente com base no `.bib`.

Exemplo de conteúdo gerado com o plugin ou por template:

```markdown
# Potential Theory in Gravity and Magnetic Applications

**Autor(es):** Richard J. Blakely  
**Ano:** 1995  
**Editora:** Cambridge University Press  
**DOI:** 10.1017/CBO9780511549816  
**Tipo:** Livro  

---

## 🧠 Resumo

## 📌 Pontos importantes

## 📚 Citações úteis

> “...” — Blakely, 1995.

## 🔗 Usado em

- [[01-Projetos/dissertacao]]
- [[04-Pesquisa/gravidade-modelo-airy]]
````

---

##  Integração com o plugin Citations

O plugin Citations permite:

- Inserir citações no estilo `[@blakely1995]` ou `[[blakely1995]]`
    
- Criar notas automaticamente com template
    
- Usar campos BibTeX como `title`, `author`, `DOI`, `year`, etc.
    

Para funcionar corretamente:

- O arquivo `referencias.bib` deve estar na raiz do Vault
    
- O campo `Literature note folder` nas configurações do plugin deve apontar para esta pasta
    

---

##  Boas práticas

- Use o plugin Citations para manter a padronização automática
    
- Conecte referências a leituras (`03-Leituras`) e projetos (`01-Projetos`)
    
- Prefira um `template-referencia.md` com os campos que você considera essenciais
    
- Inclua seus próprios comentários críticos, além dos metadados da fonte




---


