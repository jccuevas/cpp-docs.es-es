---
title: "_U_RECT Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::_U_RECT"
  - "_U_RECT"
  - "ATL._U_RECT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_U_RECT class"
  - "U_RECT class"
ms.assetid: 5f880a2d-09cf-4327-bf32-a3519c4dcd63
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# _U_RECT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase de adaptador de argumento permite punteros o referencias de `RECT` que se pasarán a una función que se implemente en términos de punteros.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class _U_RECT  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[\_U\_RECT::\_U\_RECT](../Topic/_U_RECT::_U_RECT.md)|el constructor.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[\_U\_RECT::m\_lpRect](../Topic/_U_RECT::m_lpRect.md)|Puntero a `RECT`.|  
  
## Comentarios  
 La clase define dos sobrecargas del constructor: uno acepta un argumento de **RECT&** y el otro acepta un argumento de `LPRECT` .  El primer constructor almacena la dirección del argumento de referencia en el único miembro de datos de la clase, [m\_lpRect](../Topic/_U_RECT::m_lpRect.md).  El argumento al constructor del puntero se almacena directamente sin conversión.  
  
## Requisitos  
 **encabezado:** atlwin.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)