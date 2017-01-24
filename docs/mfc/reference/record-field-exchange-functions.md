---
title: "Funciones de intercambio de campos de registros | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DAO (objetos de acceso a datos), intercambio de campos de registros (DFX)"
  - "ODBC, funciones de intercambio de datos de RFX masivo"
  - "RFX (intercambio de campos de registros), clases ODBC"
  - "DFX (intercambio de campos de registros DAO), funciones de intercambio de datos"
  - "DFX (funciones)"
  - "funciones de RFX masivo"
  - "DFX (intercambio de campos de registros DAO)"
  - "RFX (intercambio de campos de registros), clases DAO"
  - "ODBC, RFX"
  - "RFX (intercambio de campos de registros), funciones de intercambio de datos"
  - "RFX (intercambio de campos de registros)"
ms.assetid: 6e4c5c1c-acb7-4c18-bf51-bf7959a696cd
caps.latest.revision: 13
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Funciones de intercambio de campos de registros
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema muestra las funciones de intercambio de campos de registros \([RFX](#_mfc_rfx_functions_.28.odbc.29), [RFX masivo](#_mfc_bulk_rfx_functions_.28.odbc.29) y [DFX](#_mfc_dfx_functions_.28.dao.29)\) usadas para automatizar la transferencia de datos entre un objeto de conjunto de registros y su origen de datos y para realizar otras operaciones en los datos.  
  
 Si está usando las clases basadas en ODBC y ha implementado la obtención masiva de filas, debe reemplazar manualmente la función miembro `DoBulkFieldExchange` de `CRecordset` por las funciones de RFX masivo para cada miembro de datos correspondiente a una columna de origen de datos.  
  
 Si no ha implementado la obtención masiva de filas en las clases basadas en ODBC, o si está usando las clases basadas en DAO, entonces ClassWizard reemplazará la función miembro `DoFieldExchange` de `CRecordset` o `CDaoRecordset` llamando a las funciones de RFX \(para las clases ODBC\) o a las funciones de DFX \(para las clases DAO\) para cada miembro de datos de campos del conjunto de registros.  
  
 Las funciones de intercambio de campos de registros transfieren datos cada vez que el marco de trabajo llama a `DoFieldExchange` o `DoBulkFieldExchange`. Cada función transfiere un tipo de datos específico.  
  
 Para obtener más información sobre cómo se usan estas funciones, vea los artículos [Intercambio de campos de registros: Funcionamiento de RFX \(ODBC\)](../../data/odbc/record-field-exchange-how-rfx-works.md). Para obtener más información sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtener registros de forma masiva \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Para las columnas de datos que enlaza dinámicamente, también puede llamar a las funciones de RFX o DFX como se explica en los artículos [Conjunto de registros: Enlazar dinámicamente columnas de datos \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md). Además, puede escribir sus propias rutinas personalizadas de RFX o DFX, como se explica en la nota técnica [43](../../mfc/tn043-rfx-routines.md) \(para ODBC\) y en la nota técnica [53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) \(para DAO\).  
  
 Para obtener un ejemplo de funciones de RFX y de RFX masivo tal y como aparecen en las funciones `DoFieldExchange` y `DoBulkFieldExchange`, vea [RFX\_Text](../Topic/RFX_Text.md) y [RFX\_Text\_Bulk](../Topic/RFX_Text_Bulk.md). Las funciones de DFX son muy similares a las funciones de RFX.  
  
### Funciones de RFX \(ODBC\)  
  
|||  
|-|-|  
|[RFX\_Binary](../Topic/RFX_Binary.md)|Transfiere matrices de bytes del tipo [CByteArray](../../mfc/reference/cbytearray-class.md).|  
|[RFX\_Bool](../Topic/RFX_Bool.md)|Transfiere datos Boolean.|  
|[RFX\_Byte](../Topic/RFX_Byte.md)|Transfiere un solo byte de datos.|  
|[RFX\_Date](../Topic/RFX_Date.md)|Transfiere los datos de fecha y hora con [CTime](../../atl-mfc-shared/reference/ctime-class.md) o **TIMESTAMP\_STRUCT**.|  
|[RFX\_Double](../Topic/RFX_Double.md)|Transfiere datos Float de doble precisión.|  
|[RFX\_Int](../Topic/RFX_Int.md)|Transfiere datos enteros.|  
|[RFX\_Long](../Topic/RFX_Long.md)|Transfiere datos enteros largos.|  
|[RFX\_LongBinary](../Topic/RFX_LongBinary.md)|Transfiere datos de objetos binarios grandes \(BLOB\) con un objeto de la clase [CLongBinary](../../mfc/reference/clongbinary-class.md).|  
|[RFX\_Single](../Topic/RFX_Single.md)|Transfiere datos Float.|  
|[RFX\_Text](../Topic/RFX_Text.md)|Transfiere datos String.|  
  
### Funciones de RFX masivo \(ODBC\)  
  
|||  
|-|-|  
|[RFX\_Binary\_Bulk](../Topic/RFX_Binary_Bulk.md)|Transfiere matrices de datos Byte.|  
|[RFX\_Bool\_Bulk](../Topic/RFX_Bool_Bulk.md)|Transfiere matrices de datos Boolean.|  
|[RFX\_Byte\_Bulk](../Topic/RFX_Byte_Bulk.md)|Transfiere matrices de un solo byte.|  
|[RFX\_Date\_Bulk](../Topic/RFX_Date_Bulk.md)|Transfiere matrices de datos del tipo **TIMESTAMP\_STRUCT**.|  
|[RFX\_Double\_Bulk](../Topic/RFX_Double_Bulk.md)|Transfiere matrices de datos de punto flotante de doble precisión.|  
|[RFX\_Int\_Bulk](../Topic/RFX_Int_Bulk.md)|Transfiere matrices de datos enteros.|  
|[RFX\_Long\_Bulk](../Topic/RFX_Long_Bulk.md)|Transfiere matrices de datos enteros largos.|  
|[RFX\_Single\_Bulk](../Topic/RFX_Single_Bulk.md)|Transfiere matrices de datos de punto flotante.|  
|[RFX\_Text\_Bulk](../Topic/RFX_Text_Bulk.md)|Transfiere matrices de datos de tipo **LPSTR**.|  
  
### Funciones de DFX \(DAO\)  
  
|||  
|-|-|  
|[DFX\_Binary](../Topic/DFX_Binary.md)|Transfiere matrices de bytes del tipo [CByteArray](../../mfc/reference/cbytearray-class.md).|  
|[DFX\_Bool](../Topic/DFX_Bool.md)|Transfiere datos Boolean.|  
|[DFX\_Byte](../Topic/DFX_Byte.md)|Transfiere un solo byte de datos.|  
|[DFX\_Currency](../Topic/DFX_Currency.md)|Transfiere datos de divisa del tipo [COleCurrency](../../mfc/reference/colecurrency-class.md).|  
|[DFX\_DateTime](../Topic/DFX_DateTime.md)|Transfiere datos de fecha y hora del tipo [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md).|  
|[DFX\_Double](../Topic/DFX_Double.md)|Transfiere datos Float de doble precisión.|  
|[DFX\_Long](../Topic/DFX_Long.md)|Transfiere datos enteros largos.|  
|[DFX\_LongBinary](../Topic/DFX_LongBinary.md)|Transfiere datos de objetos binarios grandes \(BLOB\) con un objeto de la clase `CLongBinary`. Para DAO, se recomienda que use [DFX\_Binary](../Topic/DFX_Binary.md) en su lugar.|  
|[DFX\_Short](../Topic/DFX_Short.md)|Transfiere datos enteros cortos.|  
|[DFX\_Single](../Topic/DFX_Single.md)|Transfiere datos Float.|  
|[DFX\_Text](../Topic/DFX_Text.md)|Transfiere datos String.|  
  
## Vea también  
 [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)   
 [CRecordset::DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md)   
 [CRecordset::DoBulkFieldExchange](../Topic/CRecordset::DoBulkFieldExchange.md)   
 [CDaoRecordset::DoFieldExchange](../Topic/CDaoRecordset::DoFieldExchange.md)