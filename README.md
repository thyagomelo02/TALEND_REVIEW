# A Talend Review - DATA XPTZ

1. Create a new project in Talend Data Managment Plataform:

![image](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/557f8bd1-e81d-41b9-94f1-00aa228cadec)

2. We need to define the metadata to be utilized. In this step, we must incorporate a metadata file which will be a delimited file, to our project.

![1](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/858057d2-e7cb-4840-9c7f-b408cd62d47e)

2.1. Now find your file and make it as a unix format

![2](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/c7604ffd-08f2-428d-9fb9-1460be32bf38)

2.2. Define the settings: The encoding will be specified, the header for this dataset will be set to 3, and it will be configured as a delimited file. 

![3](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/eafdccbc-27b7-4c63-b40c-3f18b9b30bcf)

2.3 Define the schema: In this step, we will establish the metadata definitions for each column in the dataset, specifying data types such as float, int, string, etc.

![4](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/8be23053-3348-4d9a-bec1-21bf5236ce90)

3. Now in **Repository -> metadata** add a excel file:

![image](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/79ae5cce-5e04-4016-9f55-bcb25e4597c5)

3.1. Find the excel dataset file:

![5](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/8de26f2d-510c-4e02-ad59-5d5def6c4209)

3.2. Define schema: 

![7](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/9b4f0b93-a57a-43b2-bc59-302575209b6e)

4. Creating a new job. In this phase, we'll initiate a data integration task. Navigate to Repository -> Job Designs to generate a job and assign it a name.

![8](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/4b235bec-259a-4ac2-8b2a-6bda4ca32d90)

5. Drag and drop the initial file added into the job tab. Then, incorporate a component labeled **"tFileInputDelimited"**.
   
![9](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/60297bf9-c335-4987-970b-c5a1c9a8ae05)

6. Next, connect a new component, **"tLogRow"**, to the initial component.
   
![10](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/73319a09-428e-4ecb-829a-97d6f78d5093)

7. Press F6 to execute the project and review the logs in the LogRow component. This step enables the identification of errors and other issues within the dataset file.

![11](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/a71b6698-fce6-481d-a7d0-1e848939271b)

8. Drag-and-drop the excel file in the job tab:

![image](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/a65dd963-84a3-4f59-b3b3-601311fc060d)

9. Now, in **Palette -> Processing** include the "tMap" component to facilitate mapping and establish correlations between the files.

![12](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/7385442b-9cd5-4c04-b180-575cf94dfd76)

10. Access the **"tMap"** component and establish a relationship between the fields **Direcao and NAME_DIRECTOR**.
    
![14](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/53c9a2a2-f14c-4e1d-abb6-62dc951aa940)

12. Within the **tMap** component, under **"Auto Map,"** designate an output. This output will generate a table representing the income by director.

![15](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/2cfe517d-b037-4afd-bde8-1855d329d76d)

14. Drag-and-drop the following fields to new table: **Renda_R, Publico, ID_Director, Name_Director**

![16](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/b056097f-a44b-41cb-a005-a617d5cc688e)

15. Now, add a component **tAggregateRow** by **"income director row"** to make group by feature.

![17](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/ef5d54cd-6573-4249-a7ae-bc13045d9f7c)

16. **tAggregateRow** by **"income director row"**
![18](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/11ad6667-6f7d-4561-932f-755a648384e8)

17. Incorporate the columns and **synchronize** them. Then, in the Operations section, apply the **"sum"** function to the **Renda_R** field and the "**AVG**" function to the **Publico** field.

![19](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/678f8469-9e81-4653-8bb1-575962e6256d)

18. Add a new component **tLogRow** in the mode table:

![20](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/906542fa-bf55-4c53-9c7c-fae342cea0c4)

19. Run F6 the project to see the data the **income_director** table:

![22](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/276716be-2427-4df9-b5c4-f75723bafcd0)

20. Insert a **tSortRow** component between the **tAggregateRow** and **tLogRow_3** components to **sort** our data.

![23](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/ed755475-725d-4823-bf85-c1b6ee7f6641)

21. Order by **ID_DIRECTOR**

![24](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/ed7e3753-a014-46ba-bc7d-3127faba1a9b)

22. Run again the project:

![25](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/ede9abd7-b465-4c95-aa7b-c5745fbea9e8)

23. The table **"Incomes Director"** contains numerous NULL data points due to the absence of an **inner join**. Let's correct this. Return to the **tMap** component. In the excel file "**row3**", access the **tMap settings** to view the lookup configuration. Within the **Join Model**, designate it as an **Inner Join **

![26](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/7c8f2084-5eb3-4e22-b22a-89cf8fefbaca)

25. Run the project again and that will be possible to see the difference between the quantity of row in **tMap** and **tAggregateRow**

**Old Run:**
![image](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/09871ce4-ed74-4fb6-9372-003914b8d821)

**New Run**
![image](https://github.com/thyagomelo02/TALEND_REVIEW/assets/31568098/cdc1421e-e463-4de5-8c1a-473bb88e0b5c)

27. 
