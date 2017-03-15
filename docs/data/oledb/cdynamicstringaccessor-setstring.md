---
title: "CDynamicStringAccessor::SetString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicStringAccessor::SetString"
  - "CDynamicStringAccessor.SetString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetString (método)"
ms.assetid: 94846d8b-4c1b-47fe-acdc-1752981cee25
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# CDynamicStringAccessor::SetString
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece los datos de columna especificados como cadena.  
  
## Sintaxis  
  
```  
HRESULT SetString(  
   DBORDINAL nColumn,  
   BaseType* data  
) throw( );  
HRESULT SetString(  
   const CHAR* pColumnName,  
   BaseType* data  
) throw( );  
HRESULT SetString(  
   const WCHAR* pColumnName,  
   BaseType* data  
) throw( );  
```  
  
#### Parámetros  
 `nColumn`  
 \[in\] El número de columnas.  Los números de columnas empiezan por 1.  El valor especial de 0 hace referencia a la columna de marcador, si la hay.  
  
 `pColumnName`  
 \[in\] Un puntero a una cadena de caracteres que contiene el nombre de columna.  
  
 `data`  
 \[in\] Un puntero a los datos de cadena que se van a escribir en la columna especificada.  
  
## Valor devuelto  
 Un puntero al valor de cadena para el que establecer la columna especificada.  El valor es de `BaseType`escrito, dependiendo de las que sea `CHAR` o `WCHAR` si `_UNICODE` está definido o no.  
  
## Comentarios  
 El segundo formulario de reemplazo toma el nombre de columna como una cadena ANSI y el tercer formulario de reemplazo toma el nombre de columna como cadena Unicode.  
  
 Si `_SECURE_ATL` se define para tener un valor distinto de cero, se genera un error de aserción en tiempo de ejecución si la cadena de `data` de entrada es mayor que la longitud máxima permitida de la columna de datos a la que se hace referencia.  Si no, la cadena de entrada se truncada si es mayor que la longitud máxima permitida.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDynamicStringAccessor \(Clase\)](../../data/oledb/cdynamicstringaccessor-class.md)