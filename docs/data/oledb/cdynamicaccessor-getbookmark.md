---
title: "CDynamicAccessor::GetBookmark | Microsoft Docs"
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
  - "CDynamicAccessor.GetBookmark"
  - "GetBookmark"
  - "CDynamicAccessor::GetBookmark"
  - "ATL.CDynamicAccessor.GetBookmark"
  - "ATL::CDynamicAccessor::GetBookmark"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetBookmark (método)"
ms.assetid: 6d0a2970-0c62-4a34-bac7-149d8e990f81
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicAccessor::GetBookmark
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera el marcador para la fila actual.  
  
## Sintaxis  
  
```  
  
      HRESULT GetBookmark(   
   CBookmark< >* pBookmark    
) const throw( );  
```  
  
#### Parámetros  
 `pBookmark`  
 \[out\] Un puntero al objeto de [CBookmark](../../data/oledb/cbookmark-class.md) .  
  
## Valor devuelto  
 Uno de los valores estándar de `HRESULT` .  
  
## Comentarios  
 Debe establecer **DBPROP\_IRowsetLocate** a `VARIANT_TRUE` para recuperar un marcador.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDynamicAccessor \(Clase\)](../../data/oledb/cdynamicaccessor-class.md)