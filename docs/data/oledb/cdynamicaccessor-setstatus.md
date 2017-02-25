---
title: "CDynamicAccessor::SetStatus | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicAccessor::SetStatus"
  - "ATL::CDynamicAccessor::SetStatus"
  - "CDynamicAccessor.SetStatus"
  - "ATL.CDynamicAccessor.SetStatus"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetStatus (método)"
ms.assetid: 6db82694-e87d-4bf8-a7e3-5765cf6abff9
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDynamicAccessor::SetStatus
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece el estado de la columna especificada.  
  
## Sintaxis  
  
```  
  
      bool SetStatus(   
   DBORDINAL nColumn,   
   DBSTATUS status    
) throw( );  
bool SetStatus(   
   const CHAR* pColumnName,   
   DBSTATUS status    
) throw( );  
bool SetStatus(   
   const WCHAR* pColumnName,   
   DBSTATUS status    
) throw( );  
```  
  
#### Parámetros  
 `nColumn`  
 \[in\] El número de columnas.  Los números de columnas empiezan por 1.  Un valor de 0 hace referencia a la columna de marcador, si la hay.  
  
 *status*  
 \[in\] El estado de la columna.  Vea [DBSTATUS](https://msdn.microsoft.com/en-us/library/ms722617.aspx) en *la referencia del* programador para obtener más información.  
  
 `pColumnName`  
 \[in\] Un puntero a una cadena de caracteres que contiene el nombre de columna.  
  
## Valor devuelto  
 Devuelve **true** si está establecido el estado especificado de la columna correctamente.  Si no, esta función devuelve **false**.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDynamicAccessor \(Clase\)](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicAccessor::GetStatus](../../data/oledb/cdynamicaccessor-getstatus.md)