---
title: "CDynamicParameterAccessor::GetParamLength | Microsoft Docs"
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
  - "ATL::CDynamicParameterAccessor::GetParamLength"
  - "ATL.CDynamicParameterAccessor.GetParamLength"
  - "CDynamicParameterAccessor.GetParamLength"
  - "CDynamicParameterAccessor::GetParamLength"
  - "GetParamLength"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetParamLength (método)"
ms.assetid: 04d76931-911a-4915-9c2c-ad585a9f3854
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicParameterAccessor::GetParamLength
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera la longitud del parámetro especificado almacenado en el búfer.  
  
## Sintaxis  
  
```  
  
      bool GetParamLength(  
   DBORDINAL nParam,  
   DBLENGTH* pLength  
);  
DBLENGTH* GetParamLength(   
   DBORDINAL nParam    
) const throw( );  
```  
  
#### Parámetros  
 `nParam`  
 \[in\] El parámetro número \(desplazamiento desde 1\).  El parámetro 0 se reserva por valores devueltos.  El parámetro número es el índice del parámetro basándose en su orden de SQL o la llamada a un procedimiento almacenado.  Vea [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.  
  
 `pLength`  
 \[out\] Un puntero a la variable que contiene la longitud en bytes del parámetro especificado.  
  
## Comentarios  
 La primera reemplazo devuelve **true** en correctamente o **false** en el error.  Los segundos puntos de reemplazo a memoria que contiene la longitud del parámetro.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDynamicParameterAccessor \(Clase\)](../../data/oledb/cdynamicparameteraccessor-class.md)