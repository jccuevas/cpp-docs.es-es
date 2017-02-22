---
title: "_ATL_FUNC_INFO Structure | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_ATL_FUNC_INFO"
  - "ATL::_ATL_FUNC_INFO"
  - "ATL._ATL_FUNC_INFO"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ATL_FUNC_INFO structure"
  - "ATL_FUNC_INFO structure"
ms.assetid: 441ebe2c-f971-47de-9f52-a258e8d6f88e
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# _ATL_FUNC_INFO Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Contiene la información de tipos utilizada para describir un método o propiedad de dispinterface.  
  
## Sintaxis  
  
```  
  
      struct _ATL_FUNC_INFO{  
   CALLCONV cc;  
   VARTYPE vtReturn;  
   SHORT nParams;  
   VARTYPE pVarTypes[_ATL_MAX_VARTYPES];  
};  
```  
  
## Members  
 **cc**  
 La convención de llamada.  Al utilizar esta estructura con la clase de [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) , este miembro debe ser **CC\_STDCALL**.  `CC_CDECL` es la única opción admitida en Windows CE para el campo de `CALLCONV` de la estructura de `_ATL_FUNC_INFO` .  Cualquier otro valor está no compatible para su comportamiento indefinido.  
  
 **vtReturn**  
 El tipo variable de valor devuelto de la función.  
  
 **nParams**  
 El número de parámetros de la función.  
  
 **pVarTypes**  
 Matriz de tipos variables de los parámetros de la función.  
  
## Comentarios  
 Internamente, ATL utiliza esta estructura para contener la información de una biblioteca de tipos.  Puede que necesite manipular esta estructura directamente si se proporciona la información de tipo para un controlador de eventos utilizado con la clase de [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) y la macro de [SINK\_ENTRY\_INFORMATION](../Topic/SINK_ENTRY_INFO.md) .  
  
## Ejemplo  
 Dado un método dispinterface definido en IDL:  
  
 [!code-cpp[NVC_ATL_Windowing#139](../../atl/codesnippet/CPP/atl-func-info-structure_1.idl)]  
  
 defina una estructura de `_ATL_FUNC_INFO` :  
  
 [!code-cpp[NVC_ATL_Windowing#140](../../atl/codesnippet/CPP/atl-func-info-structure_2.h)]  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [Estructuras](../../atl/reference/atl-structures.md)   
 [IDispEventSimpleImpl Class](../../atl/reference/idispeventsimpleimpl-class.md)   
 [SINK\_ENTRY\_INFO](../Topic/SINK_ENTRY_INFO.md)