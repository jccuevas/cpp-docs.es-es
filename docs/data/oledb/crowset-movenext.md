---
title: "CRowset::MoveNext | Microsoft Docs"
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
  - "ATL.CRowset<TAccessor>.MoveNext"
  - "ATL.CRowset.MoveNext"
  - "ATL::CRowset<TAccessor>::MoveNext"
  - "CRowset<TAccessor>.MoveNext"
  - "CRowset.MoveNext"
  - "CRowset<TAccessor>::MoveNext"
  - "CRowset::MoveNext"
  - "ATL::CRowset::MoveNext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MoveNext (método)"
ms.assetid: 0df3288c-2bce-494f-99c0-6344b54a4adf
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::MoveNext
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Desplaza el cursor al registro siguiente.  
  
## Sintaxis  
  
```  
  
      HRESULT MoveNext( ) throw( );   
HRESULT MoveNext(   
   LONG lSkip,   
   bool bForward = true    
) throw( );  
```  
  
#### Parámetros  
 `lSkip`  
 \[in\] El número de filas que se van a omitir antes de capturar.  
  
 `bForward`  
 \[in\] Pase **true** para avanzar al registro siguiente, **false** para desplazarse hacia atrás.  
  
## Valor devuelto  
 `HRESULT`estándar.  Al final del conjunto de filas se ha alcanzado, devuelve **DB\_S\_ENDOFROWSET**.  
  
## Comentarios  
 Captura la fila secuencial siguiente del objeto de `CRowset` , memorizar la posición anterior.  Opcionalmente, puede elegir omitir a continuación las filas de `lSkip` o para desplazarse hacia atrás.  
  
 Este método requiere establecer las siguientes propiedades antes de llamar a **Abierta** en la tabla o el comando que contiene el conjunto de filas:  
  
-   **DBPROP\_CANSCROLLBACKWARDS** debe ser `VARIANT_TRUE` si `lSkip` \< 0  
  
-   **DBPROP\_CANFETCHBACKWARDS** debe ser `VARIANT_TRUE` si `bForward` \= false  
  
 Si no \(si `lSkip` \>\= 0 y `bForward` \= true\), no es necesario establecer ninguna propiedad adicional.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CRowset \(Clase\)](../../data/oledb/crowset-class.md)   
 [CRowset::MoveFirst](../../data/oledb/crowset-movefirst.md)   
 [CRowset::MoveToBookmark](../../data/oledb/crowset-movetobookmark.md)   
 [CRowset::MovePrev](../../data/oledb/crowset-moveprev.md)   
 [CRowset::MoveLast](../../data/oledb/crowset-movelast.md)