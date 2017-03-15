---
title: "CBulkRowset::MoveToBookmark | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CBulkRowset<TAccessor>::MoveToBookmark"
  - "CBulkRowset.MoveToBookmark"
  - "MoveToBookmark"
  - "ATL.CBulkRowset.MoveToBookmark"
  - "CBulkRowset::MoveToBookmark"
  - "ATL::CBulkRowset<TAccessor>::MoveToBookmark"
  - "ATL::CBulkRowset::MoveToBookmark"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MoveToBookmark (método)"
ms.assetid: 76aab025-819e-4ecd-ae0a-d8d3fb2d2099
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CBulkRowset::MoveToBookmark
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Captura la fila marcada por un marcador o una fila de un desplazamiento especificado \(`lSkip`\) del marcador.  
  
## Sintaxis  
  
```  
  
      HRESULT MoveToBookmark(  
   const CBookmarkBase& bookmark,  
   DBCOUNTITEM lSkip = 0   
) throw( );  
```  
  
#### Parámetros  
 `bookmark`  
 \[in\] Un marcador que marca la ubicación desde la que desea capturar datos.  
  
 `lSkip`  
 \[in\] El recuento del número de filas de marcador a la fila de destino.  Si `lSkip` es cero, la primera fila capturada es la fila marcada.  Si `lSkip` es 1, la primera fila capturada es la fila después de la fila marcada.  Si es `lSkip` – 1, la primera fila capturada es la fila antes de la fila marcada.  
  
## Valor devuelto  
 Vea [IRowset::GetData](https://msdn.microsoft.com/en-us/library/ms716988.aspx) en *la referencia del*programador.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CBulkRowset \(Clase\)](../../data/oledb/cbulkrowset-class.md)