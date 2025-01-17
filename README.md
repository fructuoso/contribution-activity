# README

<details>
<summary><strong>🇧🇷 Versão em Português</strong></summary>

## Sobre o Projeto

Recentemente, tenho visto muitas discussões no LinkedIn sobre o fato de ter (ou não) um GitHub ativo como critério em processos seletivos. Este repositório é uma brincadeira para demonstrar que nem tudo o que reluz é ouro.

Para criar este repositório, utilizei um script em Bash que faz centenas (ou até milhares) de commits sobrescrevendo a data. Como resultado, em questão de minutos, meu perfil do GitHub ficou todo verde no gráfico de atividades, sem que eu tenha efetivamente escrito nenhuma lógica de negócio ou funcionalidade real.

O script abaixo é autoexplicativo e faz commits com datas que avançam diariamente, podendo gerar commits aleatórios por dia. **Não recomendo** que você utilize isso no seu repositório se a intenção é “inflar” artificialmente o histórico de contribuições. Esta é apenas uma brincadeira para mostrar que um GitHub todo verde não é necessariamente sinal de domínio de qualquer tecnologia.

## Como Funciona

1. Define uma data inicial (start_date) como a data atual e uma data final (end_date) como um ano depois.
2. Para cada dia nesse intervalo, o script:
   - Cria um timestamp no formato ISO 8601.
   - Gera um número aleatório de commits (entre 1 e 10).
   - Faz cada commit com a data sobrescrita no Git.
3. Avança a data em +1 dia, repetindo o processo até chegar na data final.

## Script

```bash
#!/usr/bin/env bash

start_date=$(date '+%Y-%m-%d')
end_date=$(date -d "+1 year" '+%Y-%m-%d')

current_date="$start_date"

# Enquanto a data atual for menor ou igual a end_date...
while [[ "$(date -d "$current_date" '+%Y%m%d')" -le "$(date -d "$end_date" '+%Y%m%d')" ]]; do
    # Converte a data atual para ISO 8601 com horário e fuso, por exemplo: 2025-01-05T12:34:56-03:00
    iso_date=$(date -d "$current_date" '+%Y-%m-%dT%H:%M:%S%z')

    # Cria uma variável com um número aleatório entre 1 e 10
    random_commits=$((RANDOM % 10 + 1))

    for ((i=1; i<=$random_commits; i++)); do
        echo "$iso_date Commit $i" >> README.md
        git commit -a -m "Commit $i" --date="$iso_date"
        sleep 1.0
    done

    # Avança 1 dia
    current_date=$(date -d "$current_date + 1 day" '+%Y-%m-%d')
done
```

## Aviso

- Esse script é apenas para fins de demonstração. Não o utilize para enganar recrutadores ou empregadores.
- Valorize sempre projetos reais, estudos e boas práticas no GitHub.

---

</details>

<details>
<summary><strong>🇺🇸 English Version</strong></summary>

## About the Project

Recently, I’ve seen many discussions on LinkedIn about whether or not having an active GitHub should be used as a criterion in recruitment processes. This repository is a playful way to show that not everything that glitters is gold.

To create this repository, I used a Bash script that can generate hundreds (or even thousands) of commits by overriding the commit date. As a result, in just a few minutes, my GitHub activity graph turned entirely green without any real business logic or functionality being added.

The script below is self-explanatory and makes commits with dates that advance daily, potentially generating random commits per day. **I do not recommend** using this in your repository if your intention is just to “artificially inflate” your contribution history. This is simply a joke to illustrate that an all-green GitHub isn’t necessarily an indicator of true expertise in any technology.

## How It Works

1. Sets a start_date to the current date and an end_date to one year ahead.
2. For each day in that range, the script:
   - Creates a timestamp in ISO 8601 format.
   - Generates a random number of commits (between 1 and 10).
   - Performs each commit with an overridden Git date.
3. Advances the date by 1 day and repeats until the end_date is reached.

## Script

```bash
#!/usr/bin/env bash

start_date=$(date '+%Y-%m-%d')
end_date=$(date -d "+1 year" '+%Y-%m-%d')

current_date="$start_date"

# While the current date is less than or equal to end_date...
while [[ "$(date -d "$current_date" '+%Y%m%d')" -le "$(date -d "$end_date" '+%Y%m%d')" ]]; do
    # Convert the current date to ISO 8601 format with time and timezone, e.g., 2025-01-05T12:34:56-03:00
    iso_date=$(date -d "$current_date" '+%Y-%m-%dT%H:%M:%S%z')

    # Create a variable with a random number between 1 and 10
    random_commits=$((RANDOM % 10 + 1))

    for ((i=1; i<=$random_commits; i++)); do
        echo "$iso_date Commit $i" >> README.md
        git commit -a -m "Commit $i" --date="$iso_date"
        sleep 1.0
    done

    # Advance 1 day
    current_date=$(date -d "$current_date + 1 day" '+%Y-%m-%d')
done
```

## Disclaimer

- This script is for demonstration purposes only. Do not use it to mislead recruiters or employers.
- Always value real projects, studies, and best practices on GitHub.

---

</details>

---

**Feito com ❤️ apenas para fins de demonstração!** / **Made with ❤️ just for demonstration purposes!**