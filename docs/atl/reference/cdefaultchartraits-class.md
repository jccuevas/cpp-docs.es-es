---
title: "CDefaultCharTraits Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDefaultCharTraits"
  - "ATL::CDefaultCharTraits<T>"
  - "ATL.CDefaultCharTraits"
  - "ATL.CDefaultCharTraits<T>"
  - "ATL::CDefaultCharTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDefaultCharTraits class"
ms.assetid: f94a3934-597f-401d-8513-ed6924ae069a
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDefaultCharTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona dos funciones estáticas para convertir los caracteres entre mayúsculas y minúsculas.  
  
## Sintaxis  
  
```  
  
      template <  
   typename T  
>  
class CDefaultCharTraits  
```  
  
#### Parámetros  
 `T`  
 El tipo de datos que se almacenan en la colección.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDefaultCharTraits::CharToLower](../Topic/CDefaultCharTraits::CharToLower.md)|\(Estático\) llame a esta función para convertir un carácter en mayúsculas.|  
|[CDefaultCharTraits::CharToUpper](../Topic/CDefaultCharTraits::CharToUpper.md)|\(Estático\) llame a esta función para convertir un carácter en minúsculas.|  
  
## Comentarios  
 Esta clase proporciona las funciones utilizadas por la clase [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md).  
  
## Requisitos  
 **encabezado:** atlcoll.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)