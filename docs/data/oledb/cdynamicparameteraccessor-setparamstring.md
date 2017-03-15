---
title: "CDynamicParameterAccessor::SetParamString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CDynamicParameterAccessor.SetParamString"
  - "ATL::CDynamicParameterAccessor::SetParamString"
  - "SetParamString"
  - "CDynamicParameterAccessor::SetParamString"
  - "CDynamicParameterAccessor.SetParamString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetParamString (método)"
ms.assetid: 77a38d23-7e33-4e5a-bda6-c12c4c3fe2e4
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDynamicParameterAccessor::SetParamString
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece los datos de cadena del parámetro especificado almacenado en el búfer.  
  
## Sintaxis  
  
```  
  
      bool SetParamString(   
   DBORDINAL nParam,   
   const CHAR* pString,   
   DBSTATUS status = DBSTATUS_S_OK    
) throw( );  
bool SetParamString(   
   DBORDINAL nParam,   
   const WCHAR* pString,   
   DBSTATUS status = DBSTATUS_S_OK    
) throw( );  
```  
  
#### Parámetros  
 `nParam`  
 \[in\] El parámetro número \(desplazamiento desde 1\).  El parámetro 0 se reserva por valores devueltos.  El parámetro número es el índice del parámetro basándose en su orden de SQL o la llamada a un procedimiento almacenado.  Vea [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.  
  
 `pString`  
 \[in\] Un puntero a los datos de cadena ANSI \(**char**\) o Unicode \(**WCHAR**\) del parámetro especificado.  Vea `DBSTATUS` en oledb.h.  
  
 *status*  
 \[in\] El estado de `DBSTATUS` del parámetro especificado.  Para obtener información sobre los valores de `DBSTATUS` , vea [Estado](https://msdn.microsoft.com/en-us/library/ms722617.aspx) en *la referencia del*programador, o la búsqueda de `DBSTATUS` en oledb.h.  
  
## Comentarios  
 Devuelve **true** en correctamente o **false** en el error.  
  
 `SetParamString` generará un error si se intenta establecer una cadena que es mayor que el tamaño máximo especificado para `pString`.  
  
 Utilice `SetParamString` para establecer datos de parámetro de cadena en el búfer.  Utilice [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para establecer datos recursos de parámetro en el búfer.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDynamicParameterAccessor \(Clase\)](../../data/oledb/cdynamicparameteraccessor-class.md)