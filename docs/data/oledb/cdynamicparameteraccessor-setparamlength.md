---
title: "CDynamicParameterAccessor::SetParamLength | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CDynamicParameterAccessor::SetParamLength"
  - "CDynamicParameterAccessor.SetParamLength"
  - "ATL.CDynamicParameterAccessor.SetParamLength"
  - "CDynamicParameterAccessor::SetParamLength"
  - "SetParamLength"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetParamLength (método)"
ms.assetid: d8e0bbfe-e1ae-4a8f-9567-584fbb0c8385
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDynamicParameterAccessor::SetParamLength
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece la longitud del parámetro especificado almacenado en el búfer.  
  
## Sintaxis  
  
```  
  
      bool SetParamLength(  
   DBORDINAL nParam,  
   DBLENGTH length  
);  
```  
  
#### Parámetros  
 `nParam`  
 \[in\] El parámetro número \(desplazamiento desde 1\).  El parámetro 0 se reserva por valores devueltos.  El parámetro número es el índice del parámetro basándose en su orden de SQL o la llamada a un procedimiento almacenado.  Vea [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.  
  
 *length*  
 \[in\] La longitud en bytes del parámetro especificado.  
  
## Comentarios  
 Devuelve **true** en correctamente o **false** en el error.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDynamicParameterAccessor \(Clase\)](../../data/oledb/cdynamicparameteraccessor-class.md)