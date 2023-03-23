USE [ION_Data]
GO

/****** Object:  View [dbo].[valores_relatorio_combustivel_gas2]    Script Date: 21/03/2023 14:38:38 ******/
SET ANSI_NULLS ON
GO

SET QUOTED_IDENTIFIER ON
GO







ALTER     VIEW [dbo].[valores_relatorio_combustivel_gas2]
AS

(

SELECT DISTINCT 
	V.SEQ, 
	V.USINA, 
	V.ID_USINA, 
	V.LOCADORA, 
	V.ID_LOCADORA, 
	cast(Sum(isnull(V.QuantityID,0)) as smallint) AS QuantityID, 
	V.NUMERO_SERIE, 
	V.COD_ELETROBRAS, 
	V.data, 
	V.dataUTC, 
	Sum(isnull(V.Consumo,0)) AS Consumo,
	Sum(isnull(V.Valor_Dia_Anterior,0)) AS Valor_Dia_Anterior,
	Sum(isnull(V.pcs,0)) AS pcs,
	Sum(isnull(V.pci,0)) AS pci
FROM 

(
			SELECT DISTINCT 
					V.SEQ, 
					V.USINA, 
					V.ID_USINA, 
					V.LOCADORA, 
					V.ID_LOCADORA, 
					V.QuantityID, 
					V.NUMERO_SERIE, 
					V.COD_ELETROBRAS, 
					V.data, 
					V.dataUTC, 
					
				isnull(V.Value,0) AS Consumo,
				isnull(0,0) AS Valor_Dia_Anterior,
				isnull(0,0) AS pcs,
				isnull(0,0) AS pci
				FROM 
					dbo.view_valores AS V 
					INNER JOIN dbo.parametros AS P ON P.QUANTITYID = V.QuantityID AND V.ELEMENTOS = P.ELEMENTOS AND P.NOME = 'v_PERPETUA_D' 
					
					union all
					
				SELECT DISTINCT 
					V.SEQ, 
					V.USINA, 
					V.ID_USINA, 
					V.LOCADORA, 
					v.ID_LOCADORA, 
					0 QuantityID, 
					V.NUMERO_SERIE, 
					V.COD_ELETROBRAS, 
					V.data, 
					V.dataUTC, 
					
				isnull(0,0) AS Consumo,
				isnull(V.Value,0) AS Valor_Dia_Anterior,
				isnull(0,0) AS pcs,
				isnull(0,0) AS pci
				FROM 
					dbo.view_valores AS V 
					INNER JOIN dbo.parametros AS P ON P.QUANTITYID = V.QuantityID AND V.ELEMENTOS = P.ELEMENTOS AND P.NOME = 'v_PERPETUA_Dia_Anterior' 
					
					union all 

					SELECT DISTINCT 
					V.SEQ, 
					V.USINA, 
					V.ID_USINA, 
					V.LOCADORA, 
					V.ID_LOCADORA, 
					0 QuantityID, 
					V.NUMERO_SERIE, 
					V.COD_ELETROBRAS, 
					V.data, 
					V.dataUTC, 
					
				isnull(0,0) AS Consumo,
				isnull(0,0) AS Valor_Dia_Anterior,
				isnull(V.Value,0) AS pcs,
				isnull(0,0) AS pci
				FROM 
					dbo.view_valores AS V 
					INNER JOIN dbo.parametros AS P ON P.QUANTITYID = V.QuantityID AND V.ELEMENTOS = P.ELEMENTOS AND P.NOME = 'PCS' 
					
					union all

					SELECT DISTINCT 
					V.SEQ, 
					V.USINA, 
					V.ID_USINA, 
					V.LOCADORA, 
					V.ID_LOCADORA, 
					100 QuantityID, 
					V.NUMERO_SERIE, 
					V.COD_ELETROBRAS, 
					V.data, 
					V.dataUTC, 
					
				isnull(0,0) AS Consumo,
				isnull(0,0) AS Valor_Dia_Anterior,
				isnull(0,0) AS pcs,
				isnull(V.Value,0) AS pci
				FROM 
					dbo.view_valores AS V 
					INNER JOIN dbo.parametros AS P ON P.QUANTITYID = V.QuantityID AND V.ELEMENTOS = P.ELEMENTOS AND P.NOME = 'PCI' 
					

) V
group by V.SEQ, 
	V.USINA, 
	V.ID_USINA, 
	V.LOCADORA, 
	V.ID_LOCADORA, 
	V.NUMERO_SERIE, 
	V.COD_ELETROBRAS, 
	V.data, 
	V.dataUTC


	)
GO


