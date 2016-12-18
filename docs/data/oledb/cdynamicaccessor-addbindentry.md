---
title: "CDynamicAccessor::AddBindEntry | Microsoft Docs"
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
  - "ATL::CDynamicAccessor::AddBindEntry"
  - "AddBindEntry"
  - "CDynamicAccessor.AddBindEntry"
  - "CDynamicAccessor::AddBindEntry"
  - "ATL.CDynamicAccessor.AddBindEntry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddBindEntry (método)"
ms.assetid: 8f139376-7db3-4193-ba3b-63fe938ffa79
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicAccessor::AddBindEntry
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Agrega una entrada de enlace a las columnas de salida.  
  
## Sintaxis  
  
```  
  
      HRESULT AddBindEntry(   
   const DBCOLUMNINFO& info    
) throw( );  
```  
  
#### Parámetros  
 `info`  
 \[in\] Una estructura de **DBCOLUMNINFO** que contiene información de la columna.  Vea “estructuras de DBCOLUMNINFO” en [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx) en *la referencia del*programador.  
  
## Valor devuelto  
 Uno de los valores estándar de `HRESULT` .  
  
## Comentarios  
 Utilice este método al reemplazar el descriptor de acceso predeterminado creado con `CDynamicAccessor` \(vea [¿Cómo capturo datos?](../../data/oledb/fetching-data.md)\).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDynamicAccessor \(Clase\)](../../data/oledb/cdynamicaccessor-class.md)