# Projeto Power com Dados do ENEM 2019

## O que foi praticado?

### ETL e Boas Práticas

- A base de dados original vem de um arquivo CSV com mais de 5 milhões de linhas.  
- Por ser um arquivo pesado, a melhor prática é **não usar a base completa diretamente no Power BI**, evitando travamentos e perda de desempenho.  
- O mais coerente é **filtrar a base para trabalhar com uma amostra menor** inicialmente, e depois, ao finalizar, alterar para a base completa via parâmetros.

### Passo a passo do projeto

1. **Análise exploratória dos dados:**  
   - Criamos uma cópia filtrada da base original, selecionando dados apenas do estado de Santa Catarina (SC) para facilitar o trabalho.

2. **Estruturação dos dados no Power BI:**  
   - Todos os arquivos foram mantidos na mesma pasta, garantindo melhor integração e performance.  
   - No Power Query, renomeamos a base de dados principal como **Base de Dados Enem**. Em seguida, desabilitamos sua carga e criamos referências para essa base.  
   - Criamos um parâmetro chamado **Tipo Base**, em formato lista, contendo os nomes dos arquivos: **Base Completa** e **Base Filtrada**. O padrão ficou definido como **Base Filtrada**.  
   - Na etapa de navegação, alteramos a fonte original para usar esse parâmetro, via linguagem M:  
     ```m
     Fonte = Csv.Document(File.Contents(FolderPath & TipoBase & ".csv"))
     ```  
   - Isso permite escolher manualmente qual base utilizar, sem precisar mudar o código.

3. **Modelagem e tratamento dos dados:**  
   - Criamos a referência chamada **Tabelão**, que puxa os dados da base filtrada, contendo todos os inscritos.  
   - Tratamos os dados, mantendo somente as colunas necessárias para o modelo e garantindo integridade.  
   - Criamos tabelas dimensão, algumas extraídas da tabela fato, outras do tipo **DE-PARA** para facilitar o relacionamento entre tabelas.  
   - Construímos uma tabela calendário simples, já que os dados são de um único ano (2019).  

4. **Visualização:**  
   - Após finalizar o modelo, iniciamos a criação do dashboard para análise dos dados.

---

## Como usar este projeto

1. Coloque os arquivos CSV na mesma pasta para garantir integração e performance no Power BI.  
2. Abra o Power BI e conecte-se ao arquivo usando a configuração do parâmetro **Tipo Base** para escolher entre a base completa ou a filtrada.  
3. Faça os ajustes necessários para seu ambiente e dados, mantendo o padrão de boas práticas para arquivos grandes.  
4. Explore o dashboard e os relatórios criados para análise dos dados do ENEM 2019.

---

## Feedback

Fique à vontade para testar o dashboard e enviar seu feedback, seja ele positivo ou construtivo. Estou aberto para ajudar e aprimorar o projeto.

Obrigado!

