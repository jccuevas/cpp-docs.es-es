---
title: "CDynamicAccessor::GetValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetValue"
  - "CDynamicAccessor::GetValue<ctype>"
  - "ATL.CDynamicAccessor.GetValue<ctype>"
  - "CDynamicAccessor.GetValue"
  - "CDynamicAccessor::GetValue"
  - "ATL.CDynamicAccessor.GetValue"
  - "ATL::CDynamicAccessor::GetValue"
  - "ATL::CDynamicAccessor::GetValue<ctype>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetValue (método)"
ms.assetid: 553f44af-68bc-4cb6-8774-e0940003fa90
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDynamicAccessor::GetValue
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera datos para una columna especificada.  
  
## Sintaxis  
  
```  
  
      void* GetValue(   
   DBORDINAL nColumn    
) const throw( );  
void* GetValue(  
   const CHAR* pColumnName   
) const throw( );  
void* GetValue(  
   const WCHAR* pColumnName   
) const throw( );  
template < class ctype >  
bool GetValue(  
   DBORDINAL nColumn,  
   ctype* pData   
) const throw( );  
template < class ctype >  
bool GetValue(  
   const CHAR* pColumnName,  
   ctype* pData   
) const throw( );  
template < class ctype >  
bool GetValue(  
   const WCHAR* pColumnName,  
   ctype* pData   
) const throw( );  
```  
  
#### Parámetros  
 `ctype`  
 \[in\] Un parámetro con plantillas que controla cualquier tipo de datos excepto los tipos string \(**CHAR\***, **WCHAR\***\), que requieren un control especial.  `GetValue` utiliza el tipo de datos adecuado en función de lo que se especifiquen aquí.  
  
 `nColumn`  
 \[in\] El número de columnas.  Los números de columnas empiezan por 1.  Un valor de 0 hace referencia a la columna de marcador, si la hay.  
  
 `pColumnName`  
 \[in\] El nombre de columna.  
  
 `pData`  
 \[out\] El puntero al contenido de la columna especificada.  
  
## Valor devuelto  
 Si desea pasar datos de cadena, utilice las versiones nontemplated de `GetValue`.  Las versiones nontemplated de este método devuelve **void\***, que apunta a la parte del búfer que contiene los datos de columna especificados.  Devuelve **nulo** si la columna no se encuentra.  
  
 Para el resto de los tipos de datos, es más fácil usar las versiones con plantilla de `GetValue`.  Las versiones con plantilla devuelven **true** en correctamente o **false** en el error.  
  
## Comentarios  
 Utilice las versiones nontemplated para devolver las columnas que contienen cadenas y las versiones con plantilla para las columnas que contienen otros tipos de datos.  
  
 En modo de depuración, obtendrá una aserción si el tamaño de `pData` es distinto al tamaño de la columna a la que señala.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDynamicAccessor \(Clase\)](../../data/oledb/cdynamicaccessor-class.md)