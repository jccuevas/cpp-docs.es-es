---
title: "CDynamicAccessor::SetLength | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CDynamicAccessor::SetLength"
  - "CDynamicAccessor.SetLength"
  - "CDynamicAccessor::SetLength"
  - "ATL.CDynamicAccessor.SetLength"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetLength (método)"
ms.assetid: 8109ae73-04ec-4a47-be97-ba1e60080384
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDynamicAccessor::SetLength
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece la longitud de la columna especificada.  
  
## Sintaxis  
  
```  
  
      bool SetLength(   
   DBORDINAL nColumn,   
   DBLENGTH nLength    
) throw( );  
bool SetLength(   
   const CHAR* pColumnName,   
   DBLENGTH nLength    
) throw( );  
bool SetLength(   
   const WCHAR* pColumnName,   
   DBLENGTH nLength    
) throw( );  
```  
  
#### Parámetros  
 `nColumn`  
 \[in\] El número de columnas.  Los números de columnas empiezan por 1.  Un valor de 0 hace referencia a la columna de marcador, si la hay.  
  
 `nLength`  
 \[in\] La longitud de la columna en bytes.  
  
 `pColumnName`  
 \[in\] Un puntero a una cadena de caracteres que contiene el nombre de columna.  
  
## Valor devuelto  
 Devuelve **true** si la longitud especificada de la columna se establece correctamente.  Si no, esta función devuelve **false**.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDynamicAccessor \(Clase\)](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicAccessor::GetLength](../../data/oledb/cdynamicaccessor-getlength.md)