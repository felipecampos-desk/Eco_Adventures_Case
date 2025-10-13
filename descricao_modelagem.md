# Descrição da Modelagem de Dados

Este documento descreve a estrutura das tabelas do banco de dados para o projeto, detalhando o propósito de cada uma e seus principais atributos.

---

## **Tabela `oferta`**
Esta é a tabela principal do sistema. Ela representa um produto ou serviço, como uma atividade ou hospedagem, que pode ser reservado.
* **`id_oferta`**: Identificador único para cada oferta (chave primária).
* **`descricao`**: Uma descrição detalhada da oferta.
* **`nome`**: O nome da oferta.
* **`preco`**: O preço da oferta.
* **`tipo_experiencia`**: Define o tipo de experiência, como "Hospedagem" ou "Atividade".
* **`id_operador`**: Chave estrangeira que conecta a oferta ao operador responsável.

---

## **Tabela `reserva`**
Armazena informações sobre as reservas feitas pelos clientes.
* **`id_reserva`**: Identificador único da reserva (chave primária).
* **`data_reserva`**: A data em que a reserva foi feita.
* **`qtd_pessoas`**: Quantidade de pessoas na reserva.
* **`status`**: O status atual da reserva (ex: "Confirmada", "Pendente").
* **`id_oferta`**: Chave estrangeira que liga a reserva a uma oferta específica.
* **`id_cliente`**: Chave estrangeira que liga a reserva a um cliente.

---

## **Tabela `cliente`**
Contém os dados dos clientes que utilizam o sistema.
* **`id_cliente`**: Identificador único do cliente (chave primária).
* **`nome`**: Nome completo do cliente.
* **`email`**: E-mail de contato.
* **`data_nascimento`**: Data de nascimento.
* **`genero`**: Gênero do cliente.
* **`localidade`**: A cidade ou localidade do cliente.

---

## **Tabela `avaliacao`**
Guarda as notas e feedbacks que os clientes dão sobre as ofertas.
* **`id_avaliacao`**: Identificador único da avaliação (chave primária).
* **`nota`**: A nota dada pelo cliente.
* **`feedback`**: O comentário escrito.
* **`data_avaliacao`**: A data em que a avaliação foi registrada.
* **`id_oferta`**: Chave estrangeira que associa a avaliação a uma oferta.
* **`id_cliente`**: Chave estrangeira que associa a avaliação a um cliente.

---

## **Tabela `atividade`**
Detalha as ofertas que são do tipo "atividade".
* **`id_oferta`**: Chave primária e estrangeira, ligando a atividade diretamente à tabela `oferta`.
* **`nome`**: Nome da atividade.
* **`duracao`**: Duração da atividade em horas ou dias.
* **`nivel`**: O nível de dificuldade (e.g., "Fácil", "Difícil").
* **`qtd_limite`**: A quantidade máxima de participantes.
* **`preco`**: O preço da atividade.

---

## **Tabela `operador`**
Armazena informações sobre as empresas ou pessoas que oferecem as experiências.
* **`id_operador`**: Identificador único do operador (chave primária).
* **`nome`**: Nome da empresa ou do operador.
* **`localidade`**: Localização do operador.
* **`cnpj`**: O CNPJ do operador.
* **`email`**: E-mail de contato.
* **`telefone`**: Telefone de contato.

---

## **Tabela `hospedagem`**
Detalha as ofertas que são do tipo "hospedagem".
* **`id_oferta`**: Chave primária e estrangeira, ligando a hospedagem diretamente à tabela `oferta`.
* **`capacidade`**: A capacidade máxima de hóspedes.
* **`tipo_hospedagem`**: O tipo de hospedagem (e.g., "Hotel", "Pousada").

---

## **Tabela `pratica_sustentavel`**
Lista as práticas sustentáveis que podem ser associadas às ofertas.
* **`id_pratica`**: Identificador único de cada prática (chave primária).
* **`descricao`**: Descrição da prática sustentável.

---

## **Tabela `oferta_pratica`**
Esta é uma **tabela de junção** que conecta a `oferta` e a `pratica_sustentavel`. Ela foi criada para resolver o relacionamento de **muitos-para-muitos (N:N)**, permitindo que uma oferta tenha múltiplas práticas sustentáveis e que uma prática possa ser adotada por várias ofertas.
* **`id_pratica`**: Chave estrangeira que se refere a uma prática sustentável.
* **`id_oferta`**: Chave estrangeira que se refere a uma oferta.

## Mudanças aconselhadas pelos envolvidos de negócio:

### Tabela OFERTA
- nome = titulo

- tipo_experiencia = tipo_oferta

`Motivo:` usar o mesmo nome do atributo que está na tabela para análise.

### Tabela RESERVA
- inserir atributo "data_experiência" = data prevista para a experiência.

### Tabela AVALIACAO
- feedback = comentario

`Motivo:` usar o mesmo nome do atributo que está na tabela para análise.

### Tabela OPERADOR
- nome = nome_fantasia

`Motivo:` usar o mesmo nome do atributo que está na tabela para análise.

### Tabela ATIVIDADE
- nivel = nivel_dificuldade

- qtd_limite = grupo_maximo

`Motivo:` usar o mesmo nome do atributo que está na tabela para análise.

### Tabela HOSPEDAGEM
- tipo_hospedagem = tipo_acomodacao

- possui_cafe_manha (inserir na tabela)