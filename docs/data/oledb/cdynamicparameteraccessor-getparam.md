---
title: "CDynamicParameterAccessor::GetParam | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicParameterAccessor::GetParam"
  - "ATL.CDynamicParameterAccessor.GetParam"
  - "CDynamicParameterAccessor::GetParam<ctype>"
  - "CDynamicParameterAccessor.GetParam"
  - "GetParam"
  - "ATL::CDynamicParameterAccessor::GetParam<ctype>"
  - "ATL::CDynamicParameterAccessor::GetParam"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetParam (método)"
ms.assetid: 893a6bf8-7b55-4f6d-8a10-a43b13be7f56
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDynamicParameterAccessor::GetParam
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera los datos recursos para un parámetro de búfer especificado del parámetro.  
  
## Sintaxis  
  
```  
  
      template < class ctype > bool GetParam(   
   DBORDINAL nParam,   
   ctype* pData    
) const throw( );  
template < class ctype > bool GetParam(   
   TCHAR* pParamName,   
   ctype* pData    
) const throw( );  
void* GetParam(   
   DBORDINAL nParam    
) const throw( );  
void* GetParam(   
   TCHAR* pParamName    
) const throw( );  
```  
  
#### Parámetros  
 `ctype`  
 Un parámetro con plantillas que es el tipo de datos.  
  
 `nParam`  
 \[in\] El parámetro número \(desplazamiento desde 1\).  El parámetro 0 se reserva por valores devueltos.  El parámetro número es el índice del parámetro basándose en su orden de SQL o la llamada a un procedimiento almacenado.  Vea [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.  
  
 `pParamName`  
 \[in\] Nombre del parámetro.  
  
 `pData`  
 \[out\] El puntero a la memoria que contiene los datos recuperados del búfer.  
  
## Valor devuelto  
 Para las versiones nontemplated, señala la memoria que contiene los datos recuperados del búfer.  Para las versiones con plantilla, devuelve **true** en correctamente o **false** en el error.  
  
 Utilice `GetParam` para recuperar datos recursos de parámetros del búfer.  Utilice [GetParamString](../../data/oledb/cdynamicparameteraccessor-getparamstring.md) para recuperar datos del parámetro de cadena del búfer.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDynamicParameterAccessor \(Clase\)](../../data/oledb/cdynamicparameteraccessor-class.md)