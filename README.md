# Preparación de Tablas para el despliegue a producción
### Tablas que se tienen que limpiar
Se tienen que eliminar los datos de las tablas: 
1. tbMeasuresReads
### Data que tiene que estar precargada(revisar adjuntos):
1. tbBalance
2. tbBalanceList
3. tbBalanceWorkFlowsCat

> **IMPORTANTE**
Si no se encuentra registrado, se debe registrar para TUPS y Compresión como se indica a continuación:
    
```sql
--Para TUPS
INSERT INTO [dbo].[tbBalanceWorkFlowsCat]
           ([idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sBalanceWorkFlowCode]
           ,[sBalanceSubWorkFlowCode]
           ,[sBalanceWorkFlowName]
           ,[sBalanceWorkFlowDescritpion]
           ,[sStatus])
     VALUES
           ('99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'TUPs'
           ,'TUPs'
           ,'TUPs'
           ,'TRANSPORTES USOS PROPIOS'
           ,'A')
GO
--Para Compresión
INSERT INTO [dbo].[tbBalanceWorkFlowsCat]
           ([idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sBalanceWorkFlowCode]
           ,[sBalanceSubWorkFlowCode]
           ,[sBalanceWorkFlowName]
           ,[sBalanceWorkFlowDescritpion]
           ,[sStatus])
 VALUES
           ('823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'CMP'
           ,'CMP'
           ,'CMP'
           ,'Compresión de Gas Natural'
           ,'A')
GO
```
4. tbMeasuresPoints
> Los siguientes **MeasuresPoints** deben estar registrados y asociados a su entidad:
- **Energía Azteca VIII,S. de R. L. de C. V.**
  ```
  "TagRequested": "CV_BAJ_TAGCOMPUTADOR_Volumen_STD_DANT_M3_TREN_TOTAL"
  "IdMeasurePoint": "FA138E36-7BD3-4B1C-A1CE-CFAA5835749A"
  "TagRequested": "CV_BAJ_TAGCOMPUTADOR_Energia_STD_DANT_M3_TREN_TOTAL"
  "IdMeasurePoint": "FA138E36-7BD3-4B1C-A1CE-CFAA5835749A"
  ```
- **Energía San Luis de la Paz,S. A. de C. V.**
  ```
  "TagRequested": "CV_ESLP_TAGCOMPUTADOR_Volumen_STD_DANT_MJ/M3_TOTAL"
  "IdMeasurePoint": "517D5532-0831-4047-9BD0-136E13040F1E"
  "TagRequested": "CV_ESLP_TAGCOMPUTADOR_Energia_STD_DANT_MJ/M3_TOTAL"
  "IdMeasurePoint": "0C995265-606B-47B8-B4A0-71859BB54CC6"
  ```
- **Energía Chihuahua,S. A. de C. V.**
  ```
  "TagRequested": "CV_CHI_81AI8141_Volumen_STD_DANT_M3",
  "IdMeasurePoint": "9CA5F0CF-E8B9-4ABB-9EB0-06B9EB5427D7"
  "TagRequested": "CV_CHI_81AI8141_Energia_STD_DANT_MJ/M3"
  "IdMeasurePoint": "0629736D-5875-48F2-A86C-380E1D6E1C89"
  ```
- **Gasoducto La Rosita,S. de R. L. de C. V.**
  ```
  "TagRequested": "CV_LR_TOTAL_FQI-100-1_Volumen_STD_DANT_M3"
  "IdMeasurePoint": "B81599F1-9D8B-4875-AF9A-5D3D152C4FDE"
  "TagRequested": "CV_LR_TOTAL_FQI-100-1_Energia_STD_DANT_M3"
  "IdMeasurePoint": "4F2D8993-7CAD-4E41-9B34-23A002531A26"
  ```
- **Compresión Altamira,S. A. de C. V.**
  ```
  "TagRequested": "CV_ACS_AC-U9-M-UCP-2203_Volumen_STD_DANT_M3"
  "IdMeasurePoint": "15155DEF-D582-4C53-A2DF-0533B8BF271D"
  "TagRequested": "CV_ACS_AC-U9-M-UCP-2203_Energia_STD_DANT_MJ/M3"
  "IdMeasurePoint": "FF6B6FBB-86B4-482F-B780-5B61000ACB28"
  ```
- **Green Energy Libramiento**
  ```
  "TagRequested": "CV_GEL_FCM2002_Volumen_STD_DANT_M3"
  "IdMeasurePoint": "49AC8DBD-0651-48C8-B105-28ED5FE342BB"
  "TagRequested": "CV_GEL_FCM2002_Energia_STD_DANT_MJ/M3"
  "IdMeasurePoint": "7A6B65CF-F012-4CC1-AF3B-EBE5E08253B8"
  ```

### Scripts para la carga de los BalanceList y Balance

<details>

<summary>[Energía Azteca VIII,S. de R. L. de C. V.]</summary>

### Energía Azteca VIII,S. de R. L. de C. V.

```sql
------------------------------------------------------
-------------------ENERO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('475EAEC6-58C4-4339-9015-7529D4369CDD'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('1DA8A2F8-4326-43A1-9EF4-9C6E131765C5'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'475EAEC6-58C4-4339-9015-7529D4369CDD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,1
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------FEBRERO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('CA47F580-FBF5-420A-8DD8-F95F6E6AFE77'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('F679825A-69D1-4B12-AFA9-A7F9883B244A'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'CA47F580-FBF5-420A-8DD8-F95F6E6AFE77'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,2
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------MARZO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('7834B122-53E9-4F4E-8D7F-8E39AB3BF7B3'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('6630E05F-D790-44ED-86FF-1A0282AACF26'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'7834B122-53E9-4F4E-8D7F-8E39AB3BF7B3'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,3
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------ABRIL-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('D8A30944-7FB2-4144-A62A-1E3677B5B6F6'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('64ADA02F-68D5-46AA-956C-9A230CD6938B'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'D8A30944-7FB2-4144-A62A-1E3677B5B6F6'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,4
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------MAYO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('BB7ED760-E643-431A-8882-4B3EA3A5681B'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('329A66D5-E87E-404B-AEB0-807CED302E05'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'BB7ED760-E643-431A-8882-4B3EA3A5681B'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,5
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------JUNIO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('B0149F62-6230-4A51-9B2A-BBE622BF1C45'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('E481CC3C-7F7A-40FA-A213-16889771592F'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'B0149F62-6230-4A51-9B2A-BBE622BF1C45'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,6
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------JULIO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('F7D8B1BF-B2A8-4FF1-BF86-082A5550CC33'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('D99F0D62-1634-432B-8470-6E4789DCD218'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'F7D8B1BF-B2A8-4FF1-BF86-082A5550CC33'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,7
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------AGOSTO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('7C04CC65-0645-4308-BCBA-292F85ECC859'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('462B2522-BB46-4C61-9E5E-7A94A64EAC96'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'7C04CC65-0645-4308-BCBA-292F85ECC859'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,8
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------SEPTIEMBRE-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('12B8201D-FBC4-43D2-821D-010072C6884F'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('CBF47E4E-D506-4A5D-B9C3-34FA761E5F53'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'12B8201D-FBC4-43D2-821D-010072C6884F'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,9
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO


------------------------------------------------------
-------------------OCTUBRE-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('F8ECA56E-8564-45DB-9F49-E48DD57E78B0'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('B9689D44-6B03-4324-BD96-942F4FD048B9'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'F8ECA56E-8564-45DB-9F49-E48DD57E78B0'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,10
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------NOVIEMBRE-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('2C7C9C06-F0DE-4153-B363-E6172024607D'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('EDFE3893-4FF0-4CBD-9982-C0CDBBB0EE31'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'2C7C9C06-F0DE-4153-B363-E6172024607D'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,11
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------DICIEMBRE-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('37013960-6700-4B74-BD32-64AF2BEB5126'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('78E9C172-4C3D-43A5-8900-F2060A66AEC4'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'37013960-6700-4B74-BD32-64AF2BEB5126'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,12
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------ENERO-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('1E00028F-0009-4D25-B280-4BC1DB67AB98'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('F56D59EB-5496-4CF0-9059-AFC04A527C09'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'1E00028F-0009-4D25-B280-4BC1DB67AB98'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,1
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
--------------------FEBRERO-2023----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('92938CFD-67BC-4BA6-868A-CAA63BAECC47'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('28BD1CF3-32F8-4A14-A458-B416EC876E54'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'92938CFD-67BC-4BA6-868A-CAA63BAECC47'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,2
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------MARZO-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('16AA4185-E2F0-4D9B-9A8D-227255AA9AE4'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('48F5B3F2-3748-4986-9E94-123FFB0D0618'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'16AA4185-E2F0-4D9B-9A8D-227255AA9AE4'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,3
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------ABRIL-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('92E1C8C4-612C-49A7-BA41-35CD72E21135'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('FAB58978-C34C-4717-B580-D9E64045716C'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'92E1C8C4-612C-49A7-BA41-35CD72E21135'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,4
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------MAYO-2023------------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('09AB5BA9-B815-435D-9A61-1E3D4BA403B8'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('F1BA8596-BA75-459D-8E1F-58549132BBA7'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'09AB5BA9-B815-435D-9A61-1E3D4BA403B8'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,5
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------JUNIO-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('B56B9948-050A-4B8D-AA8A-43F306B96380'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('EBFF12FA-A1F7-49A0-921B-33D167D8965C'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'B56B9948-050A-4B8D-AA8A-43F306B96380'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,6
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------JULIO-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('682CEBC8-4F4B-4998-BF38-70F3BAE439EC'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('9572B25F-9966-44C6-9061-C17320834276'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'682CEBC8-4F4B-4998-BF38-70F3BAE439EC'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,7
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'A8D1390E-B45C-441B-BFD1-DDCCD93AEE18')
GO


------------------------------------------------------
---------------------AGOSTO-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('BFD97D5C-4D55-4C51-B2B4-371A6779C8F6'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('BE611C87-D780-4E7F-8C4F-971B0ABA3F11'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'BFD97D5C-4D55-4C51-B2B4-371A6779C8F6'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,8
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'A8D1390E-B45C-441B-BFD1-DDCCD93AEE18')
GO

------------------------------------------------------
---------------------SEPTIEMBRE-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('E7D5A4DF-68A2-4212-9A84-A9E7B8B3F1EE'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('FF634C70-AC95-4EEC-9D03-BDB426A71FDE'
           ,'AB80F105-7B7B-4429-91C2-DA514BF301C7'
           ,'E7D5A4DF-68A2-4212-9A84-A9E7B8B3F1EE'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,9
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'A8D1390E-B45C-441B-BFD1-DDCCD93AEE18')
GO
```

</details>
<details>

<summary>[Energía San Luis de la Paz,S. A. de C. V.]</summary>

### Energía San Luis de la Paz,S. A. de C. V.

```sql
------------------------------------------------------
-------------------ENERO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('7301D17A-1DC9-48C8-85DA-DA0E89A8A256'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('A7DBCA15-92DD-473E-BE7C-ECAC0B023CF2'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'7301D17A-1DC9-48C8-85DA-DA0E89A8A256'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,1
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------FEBRERO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('D9223D51-E8D2-488A-8068-2B7B56A47813'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('0CADE69F-3889-4393-A39C-196D2C28DE05'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'D9223D51-E8D2-488A-8068-2B7B56A47813'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,2
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------MARZO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('18C8DB39-8952-4882-A743-AFB052558338'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('280B030C-4C89-4329-9BF4-3396D2500BB7'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'18C8DB39-8952-4882-A743-AFB052558338'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,3
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------ABRIL-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('3DD9AEA2-9BC3-477B-95B4-7E740928175B'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('EBC0F4C1-AA27-429D-B928-40FEFA6EA83B'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'3DD9AEA2-9BC3-477B-95B4-7E740928175B'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,4
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------MAYO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('484A7891-7C83-4912-8C55-E4EFF2C5A7FF'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('A88F455F-07E8-420F-BADF-38C1F4C9A097'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'484A7891-7C83-4912-8C55-E4EFF2C5A7FF'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,5
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------JUNIO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('7997FE35-E16C-459F-A394-2A223D0D666E'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('D4D1C7B5-2955-40CF-B6C7-09D68A8E017A'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'7997FE35-E16C-459F-A394-2A223D0D666E'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,6
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------JULIO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('5FDC70FF-561F-4236-894D-3B5311BB8A52'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('51107AD2-0441-40DB-98AA-6F874B3E0DC3'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'5FDC70FF-561F-4236-894D-3B5311BB8A52'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,7
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------AGOSTO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('76F217FB-C8F3-4533-96AA-69B0EB7EF7F0'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('8371D6E6-CEC1-4BC2-B603-759B1BC4612E'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'76F217FB-C8F3-4533-96AA-69B0EB7EF7F0'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,8
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------SEPTIEMBRE-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('90B515D9-72B5-4ABC-B097-516C664783C1'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('3BE35275-3A3C-4855-B22F-6F47103BB486'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'90B515D9-72B5-4ABC-B097-516C664783C1'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,9
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO



------------------------------------------------------
-------------------OCTUBRE-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('E8D81239-41B2-4836-A9A3-12C568A3E588'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('000427BE-FF5F-48A0-8FBA-8A47655F9573'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'E8D81239-41B2-4836-A9A3-12C568A3E588'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,10
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------NOVIEMBRE-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('A21CD002-E425-4CD5-893B-94ECDB68EDCD'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('CF02771E-6961-4076-81D5-B76CE6D24573'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'A21CD002-E425-4CD5-893B-94ECDB68EDCD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,11
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------DICIEMBRE-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('9D481E66-1D28-40FE-80F6-B15C9D94FB66'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('EC0CC7A2-CD18-4A92-BF65-5348B054A9E8'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'9D481E66-1D28-40FE-80F6-B15C9D94FB66'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,12
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------ENERO-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('F4D591EB-02FF-4D36-B1AD-8B12BB37C19A'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('7D7282E8-697B-482E-A1DD-EE06A96F807D'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'F4D591EB-02FF-4D36-B1AD-8B12BB37C19A'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,1
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
--------------------FEBRERO-2023----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('B97BE39A-B50F-4F38-A4CD-2C2E16F4DAB3'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('1A4E1005-6F23-4AC4-8D21-649133A80C76'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'B97BE39A-B50F-4F38-A4CD-2C2E16F4DAB3'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,2
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------MARZO-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('818E135D-974D-4C45-BE90-C6DFFD029214'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('618C2D75-FC49-418E-BA97-8D29ECF37939'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'818E135D-974D-4C45-BE90-C6DFFD029214'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,3
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------ABRIL-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('5ECEE674-B78D-4FF1-B86C-D6C51B4B4BDD'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('1D1ACF90-3216-4509-8CC4-20937D50AB1D'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'5ECEE674-B78D-4FF1-B86C-D6C51B4B4BDD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,4
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------MAYO-2023------------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('CB27EFD9-8B36-4554-A31F-9E3F1F0B55F8'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('40391B41-899E-4BA1-AB6C-F5FBC660A43D'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'CB27EFD9-8B36-4554-A31F-9E3F1F0B55F8'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,5
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------JUNIO-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('518BFC50-57C0-4786-8D20-C2D29D49830D'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('51D38EC9-25EE-4E41-B8BD-BA107A363341'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'518BFC50-57C0-4786-8D20-C2D29D49830D'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,6
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------JULIO-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('6C713C8D-373E-4853-848C-BAFF98D5EBC8'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('6F80A32D-B832-4B9D-9751-AF64CB14701B'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'6C713C8D-373E-4853-848C-BAFF98D5EBC8'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,7
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO



------------------------------------------------------
---------------------AGOSTO-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('036E2A84-CF32-4882-BDD9-39B4A2EA4342'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('B13A6983-1FF7-40CB-83F6-4C246331CC8B'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'036E2A84-CF32-4882-BDD9-39B4A2EA4342'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,8
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'A8D1390E-B45C-441B-BFD1-DDCCD93AEE18')
GO

------------------------------------------------------
---------------------SEPTIEMBRE-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('00C42D2D-DA30-419B-BDF5-625D28E720BE'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('FDBD44CE-4C31-43DD-AA72-7EB7E08508CB'
           ,'21D9408F-4A31-48FD-9DC3-697696A253A4'
           ,'00C42D2D-DA30-419B-BDF5-625D28E720BE'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,9
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'A8D1390E-B45C-441B-BFD1-DDCCD93AEE18')
GO
```

</details>
<details>

<summary>[Gasoducto La Rosita,S. de R. L. de C. V.]</summary>

### Gasoducto La Rosita,S. de R. L. de C. V.

```sql
------------------------------------------------------
-------------------ENERO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('25376EC6-84BC-4F1F-AE79-61CEBB0259A8'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('5DF2C11E-C73C-4A9B-A150-FEDED7320CD3'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'25376EC6-84BC-4F1F-AE79-61CEBB0259A8'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,1
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------FEBRERO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('EB8E0073-F6AC-4207-8229-AB6E45847C2A'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('83D5266F-039E-4C7B-9E9C-90059CA727CE'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'EB8E0073-F6AC-4207-8229-AB6E45847C2A'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,2
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------MARZO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('A500A58A-A573-4208-A035-145B5A7B5A40'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('5B0D9615-C921-42EE-A035-7DDA8933A996'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'A500A58A-A573-4208-A035-145B5A7B5A40'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,3
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------ABRIL-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('8D01368C-082F-4B70-B306-05209B656992'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('BB49A225-0708-440E-AD2F-031EDA1606BD'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'8D01368C-082F-4B70-B306-05209B656992'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,4
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------MAYO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('2581B03E-A53E-4894-A858-C9F9CE2412D2'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('0A249FA3-C789-467A-AF90-601FC63975A4'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'2581B03E-A53E-4894-A858-C9F9CE2412D2'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,5
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------JUNIO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('DECD30F9-07DC-4DE1-A921-1369C0C45E07'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('1CAE22B1-6807-4AC9-8F29-6116EC3DE935'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'DECD30F9-07DC-4DE1-A921-1369C0C45E07'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,6
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------JULIO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('DA351986-C4F9-4EB8-A063-E29F5F9FB306'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('1F5B7C9D-9F18-44A0-8191-9F7928B2C8F4'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'DA351986-C4F9-4EB8-A063-E29F5F9FB306'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,7
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------AGOSTO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('4540CEF1-4DA3-45A1-A678-0C58ABBDB3FD'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('A42A4B61-A6BE-465D-95ED-84DC55406BE2'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'4540CEF1-4DA3-45A1-A678-0C58ABBDB3FD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,8
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------SEPTIEMBRE-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('694FE594-1CF0-4B57-A4F3-038D2F45C828'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('C6F826E9-522D-453F-B908-B686702D5E9C'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'694FE594-1CF0-4B57-A4F3-038D2F45C828'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,9
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO



------------------------------------------------------
-------------------OCTUBRE-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('D40E7D39-BD22-4181-AF58-85F549DDC52D'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('B01555F5-D258-4E77-A3FC-90EFC1033DE3'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'D40E7D39-BD22-4181-AF58-85F549DDC52D'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,10
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------NOVIEMBRE-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('939959D5-187F-4D4E-B270-1822EDAFE218'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('48854B8A-A932-42EC-8A79-F26437203339'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'939959D5-187F-4D4E-B270-1822EDAFE218'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,11
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------DICIEMBRE-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('8FEB07C8-CE48-4FCA-996B-4780B25642B7'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('A7511F8C-B058-467E-9BAB-B1B836F3CFD7'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'8FEB07C8-CE48-4FCA-996B-4780B25642B7'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,12
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------ENERO-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('EF7010C3-78AF-4265-972D-95CB2261A3D8'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('1FFA8046-C502-4BB3-980C-D9133071DBD5'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'EF7010C3-78AF-4265-972D-95CB2261A3D8'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,1
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
--------------------FEBRERO-2023----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('3A765D01-3B01-4291-9BB6-F9940E717557'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('4AB3A04E-B56F-42DC-B52C-B1CD24063075'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'3A765D01-3B01-4291-9BB6-F9940E717557'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,2
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------MARZO-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('00617860-F188-4F0F-85D4-174F834A97F2'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('55503E85-485D-4587-A984-8F47EFB9DC6D'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'00617860-F188-4F0F-85D4-174F834A97F2'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,3
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------ABRIL-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('646FF85F-9C17-405C-951A-FFD715CF8178'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('A9B54020-AEC9-4B2A-BEFC-B1162441C4E3'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'646FF85F-9C17-405C-951A-FFD715CF8178'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,4
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------MAYO-2023------------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('E3FA6302-2BB4-4C23-9440-CB1F5474C141'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('3EFF7248-8017-450E-BBEF-5F54416E4A8D'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'E3FA6302-2BB4-4C23-9440-CB1F5474C141'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,5
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------JUNIO-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('AD236C0B-EEF0-4675-87FA-3D8825BCD09D'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('A3396527-A767-44E6-9703-64698AF775D4'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'AD236C0B-EEF0-4675-87FA-3D8825BCD09D'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,6
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------JULIO-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('37618A3A-18C9-468F-AEBB-DAFDF4777FF0'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('64637DE6-6D9D-4FF4-8174-13B4ADFD66DE'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'37618A3A-18C9-468F-AEBB-DAFDF4777FF0'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,7
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO



------------------------------------------------------
---------------------AGOSTO-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('15E600AC-9C14-43E9-9D10-CCBECAD744D1'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('785A2B32-0634-464E-A321-36F17FEEF53C'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'15E600AC-9C14-43E9-9D10-CCBECAD744D1'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,8
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'A8D1390E-B45C-441B-BFD1-DDCCD93AEE18')
GO

------------------------------------------------------
---------------------SEPTIEMBRE-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('C19B8D7C-FB7F-4065-AF7A-6440BBDA13BF'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('47359A78-F7D8-4929-907E-0F4EB011E0A0'
           ,'0A823137-DBFD-434B-9A55-ABD8D1CB51D0'
           ,'C19B8D7C-FB7F-4065-AF7A-6440BBDA13BF'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,9
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'A8D1390E-B45C-441B-BFD1-DDCCD93AEE18')
GO
```

</details>
<details>

<summary>[Compresión Altamira,S. A. de C. V.]</summary>

### Compresión Altamira,S. A. de C. V.

```sql
------------------------------------------------------
-------------------ENERO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('A608C11B-12D4-4509-A354-177B88571E99'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('26769303-623A-40E9-BE20-F75E04A0FB38'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'A608C11B-12D4-4509-A354-177B88571E99'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,1
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------FEBRERO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('985D03F5-99D7-4D5C-B4A4-2ECA9079A58B'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('ABBA33F8-588A-470D-89E1-AFF938409A93'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'985D03F5-99D7-4D5C-B4A4-2ECA9079A58B'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,2
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------MARZO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('175347E2-549D-472C-828D-E70330FC2865'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('FC7D1FE8-3DB7-44B1-91EE-C7CA3CE6FCF3'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'175347E2-549D-472C-828D-E70330FC2865'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,3
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------ABRIL-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('A34454B9-0396-4027-B86F-0A7ED4E1FD5C'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('5F0D7C4D-5BF1-44DD-B4D8-3F6E8609D6CF'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'A34454B9-0396-4027-B86F-0A7ED4E1FD5C'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,4
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------MAYO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('32872896-5437-43D8-8E6D-C6135CCB4B56'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('85848B3E-28DD-473A-ABE2-81D5F0A95225'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'32872896-5437-43D8-8E6D-C6135CCB4B56'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,5
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------JUNIO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('8AA920A7-F807-46B8-AF68-4AF4ED7CFC00'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('1CD45B87-4861-4F9D-8653-EB9EF5326B13'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'8AA920A7-F807-46B8-AF68-4AF4ED7CFC00'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,6
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------JULIO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('3B6E8D88-5B67-4D9C-88BC-238D6CD0F27E'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('83AD0321-8418-4C64-A391-E9F82947F0A4'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'3B6E8D88-5B67-4D9C-88BC-238D6CD0F27E'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,7
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------AGOSTO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('129EBDD5-171A-4CF6-BA0B-BA3D434AD88B'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('3C1D3655-9F8D-4E48-A622-588A306D2ABA'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'129EBDD5-171A-4CF6-BA0B-BA3D434AD88B'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,8
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------SEPTIEMBRE-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('33FFBB61-60A8-4710-978B-19A7B099A219'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('F5D64FA1-5473-4633-8FC2-3C537E4223C7'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'33FFBB61-60A8-4710-978B-19A7B099A219'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,9
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO



------------------------------------------------------
-------------------OCTUBRE-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('3ECEE78F-21DC-4F7A-B525-81180E4CFCB8'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('0232B014-759A-482E-8E71-1302DE92BADA'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'3ECEE78F-21DC-4F7A-B525-81180E4CFCB8'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,10
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------NOVIEMBRE-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('77C919C2-7CC2-44B3-9011-80BF9D2964F0'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('1F294FCB-7516-42C9-BE4E-5CAAF390E239'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'77C919C2-7CC2-44B3-9011-80BF9D2964F0'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,11
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------DICIEMBRE-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('1C06E8F7-54DA-44CF-9783-118A7BEBE616'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('8D47599F-E7FF-46CA-8509-7532112A6D7E'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'1C06E8F7-54DA-44CF-9783-118A7BEBE616'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,12
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------ENERO-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('AE37317D-9A19-4220-8A50-B27BF375B75B'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('0A18C1BE-6ABE-42B0-8277-7CB952DA2742'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'AE37317D-9A19-4220-8A50-B27BF375B75B'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,1
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
--------------------FEBRERO-2023----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('B34A11FB-2007-435E-ADF0-970410DAB069'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('62B135D6-1281-4FCF-99E7-C534C079D0C4'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'B34A11FB-2007-435E-ADF0-970410DAB069'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,2
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------MARZO-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('01DBB142-0B97-4E92-9C28-30DB20E94C9A'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('8E1676FB-C423-41CA-BAD2-51643B8E9B42'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'01DBB142-0B97-4E92-9C28-30DB20E94C9A'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,3
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------ABRIL-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('BBEB6272-AE2E-44A1-9335-2004EF158BB7'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('F7FAD4F7-C41A-48EE-A33A-478D22597C38'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'BBEB6272-AE2E-44A1-9335-2004EF158BB7'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,4
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------MAYO-2023------------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('6297B4BC-7576-4700-8F39-392FB510FE57'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('7E91A7FA-EEC4-4F4D-A725-3E1858394E82'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'6297B4BC-7576-4700-8F39-392FB510FE57'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,5
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------JUNIO-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('2CEB6FEA-4B03-4C90-8B07-1FB52E2022F5'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('41A47CDE-5D68-463A-A8A2-7B97693AB37A'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'2CEB6FEA-4B03-4C90-8B07-1FB52E2022F5'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,6
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------JULIO-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('2016442E-2E8B-4FAF-9FFD-96490D1C0EBF'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('9B527B6B-41B9-442C-A4D5-76DD13D6946F'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'2016442E-2E8B-4FAF-9FFD-96490D1C0EBF'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,7
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO



------------------------------------------------------
---------------------AGOSTO-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('9B4A95BF-1BF9-415A-BA59-770A12DA29B0'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('CF7E86CE-19C7-422C-B30F-EBB7754FECE8'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'9B4A95BF-1BF9-415A-BA59-770A12DA29B0'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,8
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'A8D1390E-B45C-441B-BFD1-DDCCD93AEE18')
GO

------------------------------------------------------
---------------------SEPTIEMBRE-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('090BF9A4-63A6-4A23-B003-6C106A8699DC'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('56255DF1-8A0C-4B0A-88BB-902FBBC57097'
           ,'807415CD-846D-4706-8DF1-FDB6C19E85D6'
           ,'090BF9A4-63A6-4A23-B003-6C106A8699DC'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,9
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'A8D1390E-B45C-441B-BFD1-DDCCD93AEE18')
GO
```

</details>
<details>

<summary>[Green Energy Libramiento]</summary>

### Green Energy Libramiento

```sql
------------------------------------------------------
-------------------ENERO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('61F24236-9371-4524-97C8-ABEA3ED32575'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('8580839E-31D8-4CEC-B579-AD1E3A77D721'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'61F24236-9371-4524-97C8-ABEA3ED32575'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,1
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------FEBRERO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('6596B045-39B1-44ED-83FC-0BFE34860EDB'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('C728917C-F7EC-42D3-860E-DC0CA1FC92EE'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'6596B045-39B1-44ED-83FC-0BFE34860EDB'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,2
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------MARZO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('9761CDED-E656-4140-83AA-4FF5F94626AE'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('9DB71AFF-DC15-481C-918F-91B6E5526AAD'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'9761CDED-E656-4140-83AA-4FF5F94626AE'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,3
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------ABRIL-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('835E3078-9C4E-4C2E-9285-C3C3E5DC0F42'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('78ECEDFC-9E1A-4DE5-9192-ECD785E6966D'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'835E3078-9C4E-4C2E-9285-C3C3E5DC0F42'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,4
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------MAYO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('52541B1C-7B49-4CCA-9622-64B30396D7BF'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('2975AC96-E712-434F-83E4-32449C962822'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'52541B1C-7B49-4CCA-9622-64B30396D7BF'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,5
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------JUNIO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('1394FB70-825D-4624-9EB9-7BFDB2AD9D59'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('EE739C8D-A729-429E-886A-FBC0509E9EC8'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'1394FB70-825D-4624-9EB9-7BFDB2AD9D59'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,6
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------JULIO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('7C696E9B-C50E-4BFC-B45D-69AEA0DF2227'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('08638A5A-32D4-4115-A193-D7B7BDB7DE00'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'7C696E9B-C50E-4BFC-B45D-69AEA0DF2227'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,7
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------AGOSTO-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('05209F83-93DD-407A-9F4D-4612C03FB0D5'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('8C62A890-0777-44C2-B628-9854B6E2BA18'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'05209F83-93DD-407A-9F4D-4612C03FB0D5'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,8
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------SEPTIEMBRE-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('EF5B261C-6F4F-4828-B957-8553B724A80B'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('88D9CA42-A083-4722-9140-F033AFBABC37'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'EF5B261C-6F4F-4828-B957-8553B724A80B'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,9
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO





------------------------------------------------------
-------------------OCTUBRE-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('18F8DE0F-334E-462D-8AE3-D043E685C897'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('BAA925DE-25F7-46DD-ADF2-16B7F980C2BB'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'18F8DE0F-334E-462D-8AE3-D043E685C897'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,10
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------NOVIEMBRE-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('FD0D0A9F-8C78-4B74-B7AB-985AE5279F94'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
            ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('C6A8EB44-A91F-48E6-9C47-6118C0C690AD'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'FD0D0A9F-8C78-4B74-B7AB-985AE5279F94'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,11
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
-------------------DICIEMBRE-2022---------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('80E2D10C-BDC7-4D99-A4A4-764386D7C870'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('7F75B43A-C76E-4CC9-9B09-438348D5B5B9'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'80E2D10C-BDC7-4D99-A4A4-764386D7C870'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,12
           ,2022
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------ENERO-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('672A94AA-8D3A-4873-99DF-ABBEC002E941'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('0C4FACC1-428C-4458-9DC2-E94E51BD65F0'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'672A94AA-8D3A-4873-99DF-ABBEC002E941'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,1
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
--------------------FEBRERO-2023----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('CF558DCA-8ECE-42D4-B456-B6060CC61DDD'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('0B7BF98B-E856-43AE-A573-8CF14B3950BE'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'CF558DCA-8ECE-42D4-B456-B6060CC61DDD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,2
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------MARZO-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('595AD23C-843B-4561-B1A6-4B27842BF682'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('2C0ABA22-B806-4601-983B-41B65186CEC3'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'595AD23C-843B-4561-B1A6-4B27842BF682'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,3
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------ABRIL-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('EEA9CD6C-5240-4F67-85E6-BE72243E4147'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('45C94E96-0455-4619-A137-5F8EE6FFD419'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'EEA9CD6C-5240-4F67-85E6-BE72243E4147'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,4
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------MAYO-2023------------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('07DC146D-7DF8-4D52-869B-34F9954B473D'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('25485EB2-9F34-4784-9302-C6CB5263DC8E'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'07DC146D-7DF8-4D52-869B-34F9954B473D'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,5
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------JUNIO-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('462F54C7-658A-4B20-8823-4BCD053D94EF'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('103EB6F2-1A32-4E2A-B2DF-DBDEF39622EA'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'462F54C7-658A-4B20-8823-4BCD053D94EF'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,6
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
------------------------------------------------------
---------------------JULIO-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('810C1014-B0C8-4F91-A2A6-26346FEE8877'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('BCE1FD35-4741-47E9-8F16-08D8C54CC402'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'810C1014-B0C8-4F91-A2A6-26346FEE8877'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,7
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO



------------------------------------------------------
---------------------AGOSTO-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('B1DC96CB-911D-4F7E-B7FA-68105D4F12E0'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('6F3F602D-6230-4E38-824B-EECD1F3B13A1'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'B1DC96CB-911D-4F7E-B7FA-68105D4F12E0'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,8
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'A8D1390E-B45C-441B-BFD1-DDCCD93AEE18')
GO

------------------------------------------------------
---------------------SEPTIEMBRE-2023-----------------------
------------------------------------------------------
INSERT INTO [dbo].[tbBalanceList]
           ([idBalanceList]
           ,[idEntity]
           ,[idFacility]
           ,[idBalanceWorkFlow]
           ,[dCreatedOn]
           ,[idCreatedBy]
           ,[sActualStatus]
           ,[idPermit])
     VALUES
           ('7942F8CD-B7BA-4D5C-9A6C-4E74226FE000'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'D435ADBD-31DF-4763-B913-172B2CAD07DD'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'2023-07-10 19:19:58.193'
           ,'67004282-6F35-46EE-8634-8D46D3C78333'
           ,'A'
           ,'1')
GO
------------------------------------------------------
INSERT INTO [dbo].[tbBalance]
           ([idBalance]
           ,[idEntity]
           ,[idBalanceList]
           ,[idBalanceWorkFlow]
           ,[idEntityCharacterType]
           ,[sPermit]
           ,[iPeriod]
           ,[iPeriodYear]
           ,[dCreatedOn]
           ,[dLastUpdate]
           ,[idBalanceStatus])
     VALUES
           ('F502E03D-11EA-492F-AE44-6BBFAA7D39C8'
           ,'A1A28A13-25E7-4043-8332-BF1EF442A519'
           ,'7942F8CD-B7BA-4D5C-9A6C-4E74226FE000'
           ,'823D917B-2FE8-4F1D-B13B-584E9C5BF759'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,9
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'A8D1390E-B45C-441B-BFD1-DDCCD93AEE18')
GO
```

</details>
