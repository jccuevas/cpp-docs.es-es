---
title: "CRowset::MoveToBookmark | Microsoft Docs"
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
  - "ATL::CRowset::MoveToBookmark"
  - "ATL::CRowset<TAccessor>::MoveToBookmark"
  - "ATL.CRowset.MoveToBookmark"
  - "ATL.CRowset<TAccessor>.MoveToBookmark"
  - "MoveToBookmark"
  - "CRowset::MoveToBookmark"
  - "CRowset.MoveToBookmark"
  - "CRowset<TAccessor>::MoveToBookmark"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MoveToBookmark (método)"
ms.assetid: 90124723-8daf-4692-ae2f-0db26b5db920
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::MoveToBookmark
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Captura la fila marcada por un marcador o una fila de un desplazamiento especificado \(`lSkip`\) del marcador.  
  
## Sintaxis  
  
```  
  
      HRESULT MoveToBookmark(   
   const CBookmarkBase& bookmark,   
   LONG lSkip = 0    
) throw( );  
```  
  
#### Parámetros  
 `bookmark`  
 \[in\] Un marcador que marca la ubicación desde la que desea capturar datos.  
  
 `lSkip`  
 \[in\] El recuento del número de filas de marcador a la fila de destino.  Si `lSkip` es cero, la primera fila capturada es la fila marcada.  Si `lSkip` es 1, la primera fila capturada es la fila después de la fila marcada.  Si es `lSkip` – 1, la primera fila capturada es la fila antes de la fila marcada.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Este método requiere la interfaz opcional `IRowsetLocate`, que no se podría admitir en todos los proveedores; si es así, el método devuelve **E\_NOINTERFACE**.  También debe establecer **DBPROP\_IRowsetLocate** a `VARIANT_TRUE` y a **DBPROP\_CANFETCHBACKWARDS** determinado a `VARIANT_TRUE` antes de llamar a **Abierta** en la tabla o el comando que contiene el conjunto de filas.  
  
 Para obtener información sobre cómo utilizar marca una dirección de la Internet en consumidores, vea [Mediante los marcadores](../../data/oledb/using-bookmarks.md).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CRowset \(Clase\)](../../data/oledb/crowset-class.md)   
 [CRowset::MoveNext](../../data/oledb/crowset-movenext.md)   
 [CRowset::MoveFirst](../../data/oledb/crowset-movefirst.md)   
 [IRowsetLocate::GetRowsAt](https://msdn.microsoft.com/en-us/library/ms723031.aspx)   
 [CRowset::MovePrev](../../data/oledb/crowset-moveprev.md)   
 [CRowset::MoveLast](../../data/oledb/crowset-movelast.md)