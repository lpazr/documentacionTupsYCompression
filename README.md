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
--execute spAPI_GetBalanceDayTupsComp 'EBFF12FA-A1F7-49A0-921B-33D167D8965C', 'admin01'
--execute [spAPI_GetTotalCalculationTUPs] 'EBFF12FA-A1F7-49A0-921B-33D167D8965C', 'admin01'
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
```

</details>
<details>

<summary>[Energía San Luis de la Paz,S. A. de C. V.]</summary>

### Energía San Luis de la Paz,S. A. de C. V.

```sql
--execute spAPI_GetBalanceDayTupsComp 'EBFF12FA-A1F7-49A0-921B-33D167D8965C', 'admin01'
--execute [spAPI_GetTotalCalculationTUPs] 'EBFF12FA-A1F7-49A0-921B-33D167D8965C', 'admin01'
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
```

</details>
<details>

<summary>[Energía Chihuahua,S. A. de C. V.]</summary>

### Energía Chihuahua,S. A. de C. V.

```sql
--execute spAPI_GetBalanceDayTupsComp 'EBFF12FA-A1F7-49A0-921B-33D167D8965C', 'admin01'
--execute [spAPI_GetTotalCalculationTUPs] 'EBFF12FA-A1F7-49A0-921B-33D167D8965C', 'admin01'
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
           ('CD08316C-8FDE-4B3A-939C-1DF09DB959B4'
           ,'8DEE0660-0020-4862-9B07-2DC30FD5F065'
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
           ('305DABBB-FB6F-4A89-A89F-4EE5EDFAD290'
           ,'8DEE0660-0020-4862-9B07-2DC30FD5F065'
           ,'CD08316C-8FDE-4B3A-939C-1DF09DB959B4'
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
           ('DE90B6D5-9F73-497A-83AF-25A1653BCD2E'
           ,'8DEE0660-0020-4862-9B07-2DC30FD5F065'
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
           ('54370DAE-9DCA-4D71-AF4D-D05EB703ADF1'
           ,'8DEE0660-0020-4862-9B07-2DC30FD5F065'
           ,'DE90B6D5-9F73-497A-83AF-25A1653BCD2E'
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
           ('723500E9-5905-46A9-B0F0-7D9F4828C7D1'
           ,'8DEE0660-0020-4862-9B07-2DC30FD5F065'
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
           ('C2AEEE46-BD11-41D8-A4C9-67186C9AD1DA'
           ,'8DEE0660-0020-4862-9B07-2DC30FD5F065'
           ,'723500E9-5905-46A9-B0F0-7D9F4828C7D1'
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
           ('F1B942DE-AB9D-4F7E-88E3-658F18838CD8'
           ,'8DEE0660-0020-4862-9B07-2DC30FD5F065'
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
           ('F5540160-3154-4826-9799-1FB111C30D00'
           ,'8DEE0660-0020-4862-9B07-2DC30FD5F065'
           ,'F1B942DE-AB9D-4F7E-88E3-658F18838CD8'
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
           ('3C4CB6AD-1AFA-479A-A23B-421AB068E4BA'
           ,'8DEE0660-0020-4862-9B07-2DC30FD5F065'
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
           ('025A09A4-242B-4598-AF3B-0EF82FA529A3'
           ,'8DEE0660-0020-4862-9B07-2DC30FD5F065'
           ,'3C4CB6AD-1AFA-479A-A23B-421AB068E4BA'
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
           ('ECA481CF-62C1-4F44-A3FB-B8D9350E0963'
           ,'8DEE0660-0020-4862-9B07-2DC30FD5F065'
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
           ('5873296C-70AE-483F-9E19-D1AE1FE7EC42'
           ,'8DEE0660-0020-4862-9B07-2DC30FD5F065'
           ,'ECA481CF-62C1-4F44-A3FB-B8D9350E0963'
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
           ('C0AD66AD-46DB-404E-9277-42A1B839CEE6'
           ,'8DEE0660-0020-4862-9B07-2DC30FD5F065'
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
           ('CE98DB23-C68F-4BA1-B2CF-BE559CC09DD6'
           ,'8DEE0660-0020-4862-9B07-2DC30FD5F065'
           ,'C0AD66AD-46DB-404E-9277-42A1B839CEE6'
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
           ('DFED3106-60F4-4503-A676-4BE5364B7385'
           ,'8DEE0660-0020-4862-9B07-2DC30FD5F065'
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
           ('A984F554-FFC9-4251-8875-EFDEC5F10064'
           ,'8DEE0660-0020-4862-9B07-2DC30FD5F065'
           ,'DFED3106-60F4-4503-A676-4BE5364B7385'
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
           ('8EC9821F-366A-464E-82A2-A88AE8D67E19'
           ,'8DEE0660-0020-4862-9B07-2DC30FD5F065'
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
           ('24FB2A0F-78D5-434A-ACB9-E9C97A91BC4D'
           ,'8DEE0660-0020-4862-9B07-2DC30FD5F065'
           ,'8EC9821F-366A-464E-82A2-A88AE8D67E19'
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
           ('4C4FEE34-4E18-45D3-9E41-C1E96E9CAF3E'
           ,'8DEE0660-0020-4862-9B07-2DC30FD5F065'
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
           ('F75C433E-0F48-4D24-922D-309ADE77AC9D'
           ,'8DEE0660-0020-4862-9B07-2DC30FD5F065'
           ,'4C4FEE34-4E18-45D3-9E41-C1E96E9CAF3E'
           ,'99BA2F4D-FB5E-4C00-9FA6-AA6FE585DD7F'
           ,'EB5E8EF3-8F90-4772-B052-E66102384170'
           ,'SGT-78U'
           ,7
           ,2023
           ,'2023-07-10 20:15:54.657'
           ,'2023-07-10 20:15:54.657'
           ,'9BC3D15B-E989-4AE6-B286-2F7002577E4A')
GO
```

</details>
<details>

<summary>[Gasoducto La Rosita,S. de R. L. de C. V.]</summary>

### Gasoducto La Rosita,S. de R. L. de C. V.

```sql
--execute spAPI_GetBalanceDayTupsComp 'EBFF12FA-A1F7-49A0-921B-33D167D8965C', 'admin01'
--execute [spAPI_GetTotalCalculationTUPs] 'EBFF12FA-A1F7-49A0-921B-33D167D8965C', 'admin01'
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
```

</details>
<details>

<summary>[Compresión Altamira,S. A. de C. V.]</summary>

### Compresión Altamira,S. A. de C. V.

```sql
--execute spAPI_GetBalanceDayTupsComp 'EBFF12FA-A1F7-49A0-921B-33D167D8965C', 'admin01'
--execute [spAPI_GetTotalCalculationTUPs] 'EBFF12FA-A1F7-49A0-921B-33D167D8965C', 'admin01'
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
```

</details>
<details>

<summary>[Green Energy Libramiento]</summary>

### Green Energy Libramiento

```sql
--execute spAPI_GetBalanceDayTupsComp 'EBFF12FA-A1F7-49A0-921B-33D167D8965C', 'admin01'
--execute [spAPI_GetTotalCalculationTUPs] 'EBFF12FA-A1F7-49A0-921B-33D167D8965C', 'admin01'
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
```

</details>
