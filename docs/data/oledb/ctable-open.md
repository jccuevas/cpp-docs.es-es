---
title: "CTable::Open | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CTable.Open"
  - "ATL::CTable::Open"
  - "CTable::Open"
  - "CTable.Open"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Open (método)"
ms.assetid: 5d006d95-74d7-4e2b-b243-a33bc53b5455
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTable::Open
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Abra la tabla.  
  
## Sintaxis  
  
```  
  
      HRESULT Open(  
   const CSession& session,  
   LPCWSTR wszTableName,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0  
) throw ( );  
HRESULT Open(  
   const CSession& session,  
   LPCSTR szTableName,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0  
) throw ( );  
HRESULT Open(  
   const CSession& session,  
   DBID& dbid,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0  
) throw ( );  
```  
  
#### Parámetros  
 `session`  
 \[in\] Sesión para la que se abra la tabla.  
  
 *wszTableName*  
 \[in\] El nombre de la tabla a abrir, pasado como cadena Unicode.  
  
 *szTableName*  
 \[in\] El nombre de la tabla a abrir, pasado como cadena ANSI.  
  
 *dbid*  
 \[in\] **DBID** de la tabla a abrir.  
  
 *pPropSet*  
 \[in\] Un puntero a una matriz de estructuras de [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) que contienen las propiedades y los valores que se establecerán.  Vea [Conjuntos de propiedades y grupos de propiedades](https://msdn.microsoft.com/en-us/library/ms713696.aspx) en *la referencia del* programador de OLE [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  El valor predeterminado NULL no especifica ninguna propiedad.  
  
 `ulPropSets`  
 \[in\] El número de estructuras de [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) pasadas en el argumento *de pPropSet* .  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Para obtener más detalles, vea [IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx) en *la referencia del*programador.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CTable \(Clase\)](../../data/oledb/ctable-class.md)