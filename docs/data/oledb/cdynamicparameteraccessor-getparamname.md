---
title: "CDynamicParameterAccessor::GetParamName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicParameterAccessor::GetParamName"
  - "ATL.CDynamicParameterAccessor.GetParamName"
  - "GetParamName"
  - "CDynamicParameterAccessor.GetParamName"
  - "ATL::CDynamicParameterAccessor::GetParamName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetParamName (método)"
ms.assetid: 707c08ed-d3d0-4ce8-b23e-20b07202a3e2
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDynamicParameterAccessor::GetParamName
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera el nombre del parámetro especificado.  
  
## Sintaxis  
  
```  
  
      LPOLESTR GetParamName(   
   DBORDINAL nParam    
) const throw( );  
```  
  
#### Parámetros  
 `nParam`  
 \[in\] El parámetro número \(desplazamiento desde 1\).  El parámetro 0 se reserva por valores devueltos.  El parámetro número es el índice del parámetro basándose en su orden de SQL o la llamada a un procedimiento almacenado.  Vea [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.  
  
## Valor devuelto  
 El nombre del parámetro especificado.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDynamicParameterAccessor \(Clase\)](../../data/oledb/cdynamicparameteraccessor-class.md)