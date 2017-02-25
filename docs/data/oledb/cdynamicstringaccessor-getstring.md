---
title: "CDynamicStringAccessor::GetString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicStringAccessor.GetString"
  - "CDynamicStringAccessor::GetString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetString (método)"
ms.assetid: 4af27f27-7589-49f5-93d8-6ef05c023c8a
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# CDynamicStringAccessor::GetString
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera los datos de columna especificados como cadena.  
  
## Sintaxis  
  
```  
  
      BaseType* GetString(  
   DBORDINAL nColumn  
) const throw( );  
BaseType* GetString(  
   const CHAR* pColumnName  
) const throw( );  
BaseType* GetString(  
   const WCHAR* pColumnName  
) const throw( );  
```  
  
#### Parámetros  
 `nColumn`  
 \[in\] El número de columnas.  Los números de columnas empiezan por 1.  Un valor de 0 hace referencia a la columna de marcador, si la hay.  
  
 `pColumnName`  
 \[in\] Un puntero a una cadena de caracteres que contiene el nombre de columna.  
  
## Valor devuelto  
 Un puntero al valor de cadena recuperado de la columna especificada.  El valor es de ***BaseType***escrito, dependiendo de las que sea **char** o **WCHAR** si \_UNICODE está definido o no.  Devuelve NULL si la columna especificada no se encuentra.  
  
## Comentarios  
 El segundo formulario de reemplazo toma el nombre de columna como cadena ANSI.  El tercer formulario de reemplazo toma el nombre de columna como cadena Unicode.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDynamicStringAccessor \(Clase\)](../../data/oledb/cdynamicstringaccessor-class.md)