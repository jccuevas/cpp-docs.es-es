---
title: "CDynamicChain Class | Microsoft Docs"
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
  - "ATL::CDynamicChain"
  - "ATL.CDynamicChain"
  - "CDynamicChain"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDynamicChain class"
  - "chaining message maps"
  - "message maps, encadenar"
ms.assetid: f084b2be-0e77-4836-973d-ae278a1e9da8
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicChain Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos que admiten el encadenamiento dinámico de los mapas de mensajes.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CDynamicChain  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDynamicChain::CDynamicChain](../Topic/CDynamicChain::CDynamicChain.md)|el constructor.|  
|[CDynamicChain::~CDynamicChain](../Topic/CDynamicChain::~CDynamicChain.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDynamicChain::CallChain](../Topic/CDynamicChain::CallChain.md)|Envía un mensaje de Windows al mapa de mensajes de otro objeto.|  
|[CDynamicChain::RemoveChainEntry](../Topic/CDynamicChain::RemoveChainEntry.md)|Quita una entrada del mapa de mensajes de la colección.|  
|[CDynamicChain::SetChainEntry](../Topic/CDynamicChain::SetChainEntry.md)|Agrega una entrada del mapa de mensajes a la colección o modifique una entrada existente.|  
  
## Comentarios  
 `CDynamicChain` administra una colección de mapas de mensajes, habilitar un mensaje de Windows se envíen, en tiempo de ejecución, el mapa de mensajes de otro objeto.  
  
 Para agregar compatibilidad para el encadenamiento dinámico de los mapas de mensajes, haga lo siguiente:  
  
-   derive la clase de `CDynamicChain`.  En el mapa de mensajes, especifican la macro de [CHAIN\_MSG\_MAP\_DYNAMIC](../Topic/CHAIN_MSG_MAP_DYNAMIC.md) para encadenar el mapa de mensajes predeterminado de otro objeto.  
  
-   Derive cada clase que desea encadenar de [CMessageMap](../../atl/reference/cmessagemap-class.md).  `CMessageMap` permite a un objeto exponer los mapas de mensajes a otros objetos.  
  
-   Llame a `CDynamicChain::SetChainEntry` para identificar a la que el objeto y que el mensaje asigna desee encadenar.  
  
 Por ejemplo, supongamos que la clase se define como sigue:  
  
 [!code-cpp[NVC_ATL_Windowing#88](../../atl/codesnippet/CPP/cdynamicchain-class_1.h)]  
  
 El cliente llama `CMyWindow::SetChainEntry`:  
  
 [!code-cpp[NVC_ATL_Windowing#89](../../atl/codesnippet/CPP/cdynamicchain-class_2.cpp)]  
  
 donde es el objeto encadenado y es una instancia `chainedObj` de una clase derivada de `CMessageMap`.  Ahora, si `myCtl` recibe un mensaje que no está controlado por `OnPaint` o `OnSetFocus`, el procedimiento de ventana dirige el mensaje al mapa de mensajes predeterminado de los entity\_chainedObj.  
  
 Para obtener más información acerca del encadenamiento del mapa de mensajes, vea [Mapas de mensajes](../../atl/message-maps-atl.md) en el artículo “clases de ventana ATL.”  
  
## Requisitos  
 **encabezado:** atlwin.h  
  
## Vea también  
 [CWindowImpl Class](../../atl/reference/cwindowimpl-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)