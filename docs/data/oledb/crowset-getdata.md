---
title: "CRowset::GetData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CRowset<TAccessor>::GetData"
  - "ATL::CRowset<TAccessor>::GetData"
  - "ATL::CRowset::GetData"
  - "ATL.CRowset<TAccessor>.GetData"
  - "CRowset<TAccessor>.GetData"
  - "CRowset::GetData"
  - "CRowset.GetData"
  - "ATL.CRowset.GetData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetData (método) [OLE DB]"
ms.assetid: 1e0347b5-3e24-4ff8-a790-839616c1522f
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CRowset::GetData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera los datos desde la copia del conjunto de filas de la fila.  
  
## Sintaxis  
  
```  
  
      HRESULT GetData( ) throw( );   
HRESULT GetData(   
   int nAccessor    
) throw( );  
```  
  
#### Parámetros  
 `nAccessor`  
 \[in\] El número de índice \(de cero\- desplazamiento\) de descriptor de acceso necesarios para tener acceso a los datos.  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Si especifica un descriptor de acceso que no sea autoaccessor en [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md), utilice este método explícitamente para obtener los datos pasando el número de descriptor de acceso.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CRowset \(Clase\)](../../data/oledb/crowset-class.md)