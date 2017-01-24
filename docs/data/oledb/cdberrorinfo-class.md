---
title: "CDBErrorInfo (Clase) | Microsoft Docs"
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
  - "CDBErrorInfo"
  - "ATL::CDBErrorInfo"
  - "ATL.CDBErrorInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDBErrorInfo (clase)"
ms.assetid: 9a5c18a2-ee3e-40f5-ab4c-581288d7f737
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDBErrorInfo (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona compatibilidad para el procesamiento de error de OLE DB mediante la interfaz OLE DB [IErrorRecords](https://msdn.microsoft.com/en-us/library/ms718112.aspx) .  
  
## Sintaxis  
  
```  
class CDBErrorInfo  
```  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[GetAllErrorInfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md)|Devuelve toda la información de error contenida en un registro de errores.|  
|[GetBasicErrorInfo](../../data/oledb/cdberrorinfo-getbasicerrorinfo.md)|Llama a [IErrorRecords::GetBasicErrorInfo](https://msdn.microsoft.com/en-us/library/ms723907.aspx) para devolver información básica sobre el error especificado.|  
|[GetCustomErrorObject](../../data/oledb/cdberrorinfo-getcustomerrorobject.md)|Llama a [IErrorRecords::GetCustomErrorObject](https://msdn.microsoft.com/en-us/library/ms725417.aspx) para devolver un puntero a una interfaz en un objeto de error personalizado.|  
|[GetErrorInfo](../../data/oledb/cdberrorinfo-geterrorinfo.md)|Llama a [IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/en-us/library/ms711230.aspx) para devolver un puntero de interfaz de **IErrorInfo** el registro especificado.|  
|[GetErrorParameters](../../data/oledb/cdberrorinfo-geterrorparameters.md)|Llama a [IErrorRecords::GetErrorParameters](https://msdn.microsoft.com/en-us/library/ms715793.aspx) para devolver los parámetros del error.|  
|[GetErrorRecords](../../data/oledb/cdberrorinfo-geterrorrecords.md)|Obtiene los registros de errores para el objeto especificado.|  
  
## Comentarios  
 Esta interfaz devuelve uno o varios registros de error al usuario.  Llame a [CDBErrorInfo::GetErrorRecords](../../data/oledb/cdberrorinfo-geterrorrecords.md) primero, para obtener un recuento de registros de error.  Llamar a continuación a una de las funciones de acceso, como [CDBErrorInfo::GetAllErrorInfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md), información de error de recuperación para cada registro.  
  
## Requisitos  
 **Header:** atldbcli.h  
  
## Vea también  
 [DBViewer](../../top/visual-cpp-samples.md)   
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)