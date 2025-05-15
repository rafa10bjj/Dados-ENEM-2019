# Projeto Power com Dados do ENEM 2019

## O que foi praticado?

### ETL e Boas Práticas

- A base de dados original vem de um arquivo CSV com mais de 5 milhões de linhas.  
- Por ser um arquivo pesado, a melhor prática é **não usar a base completa diretamente no Power BI**, evitando travamentos e perda de desempenho.  
- O mais coerente é **filtrar a base para trabalhar com uma amostra menor** inicialmente, e depois, ao finalizar, alterar para a base completa via parâmetros.

### Passo a passo do projeto

1. **Análise exploratória dos dados:**  
   - Criamos uma cópia filtrada da base original, selecionando dados apenas do estado de Santa Catarina (SC) para facilitar o trabalho.
![Captura de tela 2025-05-15 115740](https://github.com/user-attachments/assets/c52b079b-77b8-49ec-af84-de02511aaaaf)

2. **Estruturação dos dados no Power BI:**  
   - Todos os arquivos foram mantidos na mesma pasta, garantindo melhor integração e performance.  
   - No Power Query, renomeamos a base de dados principal como **Base de Dados Enem**. Em seguida, desabilitamos sua carga e criamos referências para essa base.  
   - Criamos um parâmetro chamado **Tipo Base**, em formato lista, contendo os nomes dos arquivos: **Base Completa** e **Base Filtrada**. O padrão ficou definido como **Base Filtrada**.  
   - Na etapa de navegação, alteramos a fonte original para usar esse parâmetro, via linguagem M:  
     ```m
     Fonte = Csv.Document(File.Contents(FolderPath & TipoBase & ".csv"))
     ```
     ![Captura de tela 2025-05-15 115424](https://github.com/user-attachments/assets/58cd56fb-5c05-4c71-b5b7-6843f790ce7e)

   - Isso permite escolher manualmente qual base utilizar, sem precisar mudar o código.

3. **Modelagem e tratamento dos dados:**  
   - Criamos a referência chamada **Tabelão**, que puxa os dados da base filtrada, contendo todos os inscritos.  
   - Tratamos os dados, mantendo somente as colunas necessárias para o modelo e garantindo integridade.  
   - Criamos tabelas dimensão, algumas extraídas da tabela fato, outras do tipo **DE-PARA** para facilitar o relacionamento entre tabelas.  
   - Construímos uma tabela calendário simples, já que os dados são de um único ano (2019).  
   ![Captura de tela 2025-05-15 115450](https://github.com/user-attachments/assets/5a362571-a1c9-4f57-acb4-3ac36baaf681)
   ![Captura de tela 2025-05-15 115434](https://github.com/user-attachments/assets/7217d0a3-ad9b-4c19-bd7f-751005e130c6)


4. **Visualização:**  
   - Após finalizar o modelo, iniciamos a criação do dashboard para análise dos dados.

---

## Como usar este projeto

1. Coloque os arquivos CSV na mesma pasta para garantir integração e performance no Power BI.  
2. Abra o Power BI e conecte-se ao arquivo usando a configuração do parâmetro **Tipo Base** para escolher entre a base completa ou a filtrada.  
3. Faça os ajustes necessários para seu ambiente e dados, mantendo o padrão de boas práticas para arquivos grandes.  
4. Explore o dashboard e os relatórios criados para análise dos dados do ENEM 2019.
 ![Captura de tela 2025-05-15 115529](https://github.com/user-attachments/assets/40921994-678c-4da3-8768-22b8a56804bb)
 ![Captura de tela 2025-05-15 115546](https://github.com/user-attachments/assets/88e38617-8e21-43d9-b3b0-cc1a64d5d9db)
 ![Captura de tela 2025-05-15 115558](https://github.com/user-attachments/assets/382dd07a-27c3-45e4-a482-406667352b4a)
 ![Captura de tela 2025-05-15 115610](https://github.com/user-attachments/assets/1c1ef906-5abd-4554-b340-b52dc77ec40a)



---

## Feedback

Fique à vontade para testar o dashboard e enviar seu feedback, seja ele positivo ou construtivo. Estou aberto para ajudar e aprimorar o projeto.

Obrigado!

