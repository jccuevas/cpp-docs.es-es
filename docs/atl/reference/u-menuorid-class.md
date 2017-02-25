---
title: "_U_MENUorID Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL._U_MENUorID"
  - "ATL::_U_MENUorID"
  - "_U_MENUorID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_U_MENUorID class"
  - "U_MENUorID class"
ms.assetid: cfc8032b-61b4-4a68-ba3a-92b82500ccae
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# _U_MENUorID Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona contenedores para **CreateWindow** y **CreateWindowEx**.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class _U_MENUorID  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[\_U\_MENUorID::\_U\_MENUorID](../Topic/_U_MENUorID::_U_MENUorID.md)|el constructor.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[\_U\_MENUorID::m\_hMenu](../Topic/_U_MENUorID::m_hMenu.md)|un identificador a un menú.|  
  
## Comentarios  
 Esta clase de adaptador de argumento permite los id. \(s de**UINT**\) o identificadores de menú \(s de`HMENU`\) que se pasarán a una función sin requerir una conversión explícita del llamador.  
  
 Esta clase está diseñada para implementar contenedores de [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) y de [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) a las funciones de la API de Windows, determinado, que aceptan un argumento de `HMENU` que puede ser un identificador de ventana secundaria \(**UINT**\) en lugar de un identificador de menú.  Por ejemplo, puede ver esta clase en uso como parámetro a [CWindowImpl:: Crear](../Topic/CWindowImpl::Create.md).  
  
 La clase define dos sobrecargas del constructor: uno acepta un argumento de **UINT** y el otro acepta un argumento de `HMENU` .  El argumento de **UINT** es simplemente conversión a `HMENU` en el constructor y el resultado almacenados en el único miembro de datos de la clase, [m\_hMenu](../Topic/_U_MENUorID::m_hMenu.md).  El argumento al constructor de `HMENU` se almacena directamente sin conversión.  
  
## Requisitos  
 **encabezado:** atlwin.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)