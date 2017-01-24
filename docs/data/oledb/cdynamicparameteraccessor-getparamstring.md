---
title: "CDynamicParameterAccessor::GetParamString | Microsoft Docs"
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
  - "CDynamicParameterAccessor.GetParamString"
  - "GetParamString"
  - "CDynamicParameterAccessor::GetParamString"
  - "ATL.CDynamicParameterAccessor.GetParamString"
  - "ATL::CDynamicParameterAccessor::GetParamString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetParamString (método)"
ms.assetid: 078c2b1c-7072-47c1-a203-f47e75363f91
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicParameterAccessor::GetParamString
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera los datos de cadena del parámetro especificado almacenado en el búfer.  
  
## Sintaxis  
  
```  
  
      bool GetParamString(  
   DBORDINAL nParam,  
   CSimpleStringA& strOutput  
) throw( );  
bool GetParamString(  
   DBORDINAL nParam,  
   CSimpleStringW& strOutput  
) throw( );  
bool GetParamString(  
   DBORDINAL nParam,  
   CHAR* pBuffer,  
   size_t* pMaxLen  
) throw( );  
bool GetParamString(  
   DBORDINAL nParam,  
   WCHAR* pBuffer,  
   size_t* pMaxLen  
) throw( );  
```  
  
#### Parámetros  
 `nParam`  
 \[in\] El parámetro número \(desplazamiento desde 1\).  El parámetro 0 se reserva por valores devueltos.  El parámetro número es el índice del parámetro basándose en su orden de SQL o la llamada a un procedimiento almacenado.  Vea [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.  
  
 `strOutput`  
 \[out\] Los datos de cadena ANSI \(**CSimpleStringA**\) o Unicode \(**CSimpleStringW**\) del parámetro especificado.  Debe pasar un parámetro de `CString`tipo, por ejemplo:  
  
 [!code-cpp[NVC_OLEDB_Consumer#9](../../data/oledb/codesnippet/CPP/cdynamicparameteraccessor-getparamstring_1.cpp)]  
  
 `pBuffer`  
 \[out\] Un puntero a los datos de cadena ANSI \(**char**\) o Unicode \(**WCHAR**\) del parámetro especificado.  
  
 `pMaxLen`  
 \[out\] Un puntero al tamaño del búfer indicada por `pBuffer` \(en caracteres, incluidos el NULL que termina\).  
  
## Comentarios  
 Devuelve **true** en correctamente o **false** en el error.  
  
 Si `pBuffer` es NULL, este método establecerá el tamaño de búfer necesario en memoria designada por a `pMaxLen` y a **true** return sin copiar los datos.  
  
 Este método producirá un error si el búfer `pBuffer` no es lo bastante grande para contener la cadena completa.  
  
 Utilice `GetParamString` para recuperar datos del parámetro de cadena del búfer.  Utilice [Cdynamicparameteraccessor](../../data/oledb/cdynamicparameteraccessor-getparam.md) para recuperar datos recursos de parámetros del búfer.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDynamicParameterAccessor \(Clase\)](../../data/oledb/cdynamicparameteraccessor-class.md)