---
title: "CSession::Open | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CSession::Open"
  - "CSession::Open"
  - "CSession.Open"
  - "ATL.CSession.Open"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Open (método)"
ms.assetid: c2050c2c-9817-4857-be49-189f346968f6
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# CSession::Open
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Abre una nueva sesión del objeto de origen de datos.  
  
## Sintaxis  
  
```  
  
      HRESULT Open(  
   const CDataSource& ds,  
   DBPROPSET *pPropSet = NULL,  
   ULONG ulPropSets = 0  
) throw( );  
```  
  
#### Parámetros  
 `ds`  
 \[in\] El origen de datos que la sesión debe abrirse.  
  
 *pPropSet*  
 \[in\] Un puntero a una matriz de estructuras de [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) que contienen las propiedades y los valores que se establecerán.  Vea [Conjuntos de propiedades y grupos de propiedades](https://msdn.microsoft.com/en-us/library/ms713696.aspx) en *la referencia del* programador de OLE [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `ulPropSets`  
 \[in\] El número de estructuras de [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) pasadas en el argumento *de pPropSet* .  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Debe abrir el objeto de origen de datos mediante [CDataSource::Open](../../data/oledb/cdatasource-open.md) antes de pasarla a `CSession::Open`.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CSession \(Clase\)](../../data/oledb/csession-class.md)