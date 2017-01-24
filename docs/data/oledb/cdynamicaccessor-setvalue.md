---
title: "CDynamicAccessor::SetValue | Microsoft Docs"
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
  - "ATL.CDynamicAccessor.SetValue"
  - "ATL::CDynamicAccessor::SetValue"
  - "ATL::CDynamicAccessor::SetValue<ctype>"
  - "CDynamicAccessor.SetValue"
  - "ATL.CDynamicAccessor.SetValue<ctype>"
  - "CDynamicAccessor::SetValue"
  - "CDynamicAccessor::SetValue<ctype>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetValue (método)"
ms.assetid: ecc18850-96e5-4845-abe5-ab34ad467238
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicAccessor::SetValue
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Almacena datos a una columna especificada.  
  
## Sintaxis  
  
```  
  
      template < class ctype >    
bool SetValue(   
   DBORDINAL nColumn,   
   const ctype& data    
) throw( );  
template < class ctype >    
bool SetValue(   
   const CHAR * pColumnName,   
   const ctype& data    
) throw( );  
template <class ctype>   
bool SetValue(  
   const WCHAR *pColumnName,  
   const ctype& data   
) throw( );  
```  
  
#### Parámetros  
 `ctype`  
 \[in\] Un parámetro con plantillas que controla cualquier tipo de datos excepto los tipos string \(**CHAR\***, **WCHAR\***\), que requieren un control especial.  `GetValue` utiliza el tipo de datos adecuado en función de lo que se especifiquen aquí.  
  
 `pColumnName`  
 \[in\] Un puntero a una cadena de caracteres que contiene el nombre de columna.  
  
 `data`  
 \[in\] El puntero a la memoria que contiene los datos.  
  
 `nColumn`  
 \[in\] El número de columnas.  Los números de columnas empiezan por 1.  Un valor de 0 hace referencia a la columna de marcador, si la hay.  
  
## Valor devuelto  
 Si desea establecer datos de cadena, utilice las versiones nontemplated de `GetValue`.  Las versiones nontemplated de este método devuelve **void\***, que apunta a la parte del búfer que contiene los datos de columna especificados.  Devuelve **nulo** si la columna no se encuentra.  
  
 Para el resto de los tipos de datos, es más fácil usar las versiones con plantilla de `GetValue`.  Las versiones con plantilla devuelven **true** en correctamente o **false** en el error.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDynamicAccessor \(Clase\)](../../data/oledb/cdynamicaccessor-class.md)