---
title: "CDynamicAccessor::GetColumnFlags | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicAccessor.GetColumnFlags"
  - "ATL::CDynamicAccessor::GetColumnFlags"
  - "ATL.CDynamicAccessor.GetColumnFlags"
  - "CDynamicAccessor::GetColumnFlags"
  - "GetColumnFlags"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetColumnFlags (método)"
ms.assetid: b2ba2f3a-2c61-4a49-abfb-75823908ccf4
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDynamicAccessor::GetColumnFlags
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera las características de la columna.  
  
## Sintaxis  
  
```  
  
      bool GetColumnFlags(   
   DBORDINAL nColumn,   
   DBCOLUMNFLAGS* pFlags    
) const throw( );  
```  
  
#### Parámetros  
 `nColumn`  
 \[in\] El número de columnas.  Los números de columnas empiezan por 1.  Un valor de 0 hace referencia a la columna de marcador, si la hay.  
  
 `pFlags`  
 \[out\] Un puntero a una máscara de bits que describe las características de la columna.  Vea “tipo enumerado DBCOLUMNFLAGS de” en [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx) en *la referencia del*programador.  
  
## Valor devuelto  
 Devuelve **true** si las características de la columna se recuperan correctamente.  De lo contrario, devuelve **false.**  
  
## Comentarios  
 El número de columnas se compensa desde uno.  La columna cero es un caso especial; es el marcador si está disponible.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDynamicAccessor \(Clase\)](../../data/oledb/cdynamicaccessor-class.md)