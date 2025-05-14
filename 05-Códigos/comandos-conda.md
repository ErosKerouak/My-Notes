**Linguagem:** #Bash  

### Comandos Básicos

- `conda --version` → Exibe a versão instalada do Conda.
- `conda update conda` → Atualiza o Conda para a versão mais recente.
- `conda info` → Mostra detalhes sobre a instalação do Conda e configurações do sistema.

### Gerenciamento de Ambientes

- `conda create --name meu_ambiente` → Cria um ambiente chamado `meu_ambiente`.
- `conda activate meu_ambiente` → Ativa o ambiente virtual.
- `conda deactivate` → Sai do ambiente virtual atual.
- `conda env list ou conda info --envs` → Mostra todos os ambientes disponíveis.
- `conda remove --name meu_ambiente --all` → Apaga completamente o ambiente `meu_ambiente`.

### Exportar e Clonar Ambientes

- `conda env export > ambiente.yml` → Salva o ambiente atual no arquivo `ambiente.yml`. Isso permite que o ambiente seja recriado em outra máquina.
- `conda env create -f ambiente.yml` → Restaura um ambiente a partir do arquivo `ambiente.yml`.
- `conda create --name novo_ambiente --clone meu_ambiente` → Cria uma cópia exata do ambiente `meu_ambiente` com o nome `novo_ambiente`.

### Gerenciamento de Pacotes

- `conda list` → Exibe todos os pacotes instalados no ambiente ativo.
- `conda install pacote` → Instala o pacote no ambiente ativo.
- `conda remove pacote` → Remove o pacote do ambiente ativo.
- `conda update pacote` → Atualiza o pacote para a versão mais recente.
- `conda update --all` → Atualiza todos os pacotes do ambiente ativo para a versão mais recente.

###  Relacionado a

- [[comandos-bash-essenciais]]
- [[comandos-git]]
- [[instalação-de-programas]]
