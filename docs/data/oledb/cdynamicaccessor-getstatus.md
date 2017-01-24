---
title: "CDynamicAccessor::GetStatus | Microsoft Docs"
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
  - "ATL::CDynamicAccessor::GetStatus"
  - "CDynamicAccessor.GetStatus"
  - "ATL.CDynamicAccessor.GetStatus"
  - "CDynamicAccessor::GetStatus"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetStatus (método)"
ms.assetid: 8f1aba69-5c2c-4ca7-ad84-7b4b27995eb8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicAccessor::GetStatus
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera el estado de la columna especificada.  
  
## Sintaxis  
  
```  
  
      bool GetStatus(   
   DBORDINAL nColumn,   
   DBSTATUS* pStatus    
) const throw( );  
bool GetStatus(  
   const CHAR* pColumnName,  
   DBSTATUS* pStatus   
) const throw( );  
bool GetStatus(  
   const WCHAR* pColumnName,  
   DBSTATUS* pStatus   
) const throw( );  
```  
  
#### Parámetros  
 `nColumn`  
 \[in\] El número de columnas.  Los números de columnas empiezan por 1.  Un valor de 0 hace referencia a la columna de marcador, si la hay.  
  
 `pColumnName`  
 \[in\] Un puntero a una cadena de caracteres que contiene el nombre de columna.  
  
 `pStatus`  
 \[out\] Un puntero a la variable que contiene el estado de la columna.  Vea [DBSTATUS](https://msdn.microsoft.com/en-us/library/ms722617.aspx) en *la referencia del* programador para obtener más información.  
  
## Valor devuelto  
 Devuelve **true** si se encuentra la columna especificada.  Si no, esta función devuelve **false**.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDynamicAccessor \(Clase\)](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicAccessor::SetStatus](../../data/oledb/cdynamicaccessor-setstatus.md)