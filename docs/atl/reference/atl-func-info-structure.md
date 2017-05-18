---
title: Estructura de estructuras _ATL_FUNC_INFO | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _ATL_FUNC_INFO
- ATL::_ATL_FUNC_INFO
- ATL._ATL_FUNC_INFO
dev_langs:
- C++
helpviewer_keywords:
- _ATL_FUNC_INFO structure
- ATL_FUNC_INFO structure
ms.assetid: 441ebe2c-f971-47de-9f52-a258e8d6f88e
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 7bc607931c486f3dd7a398b277048db77e9b2f62
ms.contentlocale: es-es
ms.lasthandoff: 03/31/2017

---
# <a name="atlfuncinfo-structure"></a>Estructura de estructuras _ATL_FUNC_INFO
Contiene información de tipo que se utiliza para describir un método o propiedad en una interfaz dispinterface.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct _ATL_FUNC_INFO {
    CALLCONV cc;
    VARTYPE vtReturn;
    SHORT nParams;
    VARTYPE pVarTypes[_ATL_MAX_VARTYPES];
};
```  
  
## <a name="members"></a>Miembros  
 **CC**  
 Convención de llamada. Cuando se usa esta estructura con la [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) (clase), este miembro debe ser **CC_STDCALL**. `CC_CDECL`es la única opción admitida de Windows CE para la `CALLCONV` campo de la `_ATL_FUNC_INFO` estructura. Cualquier otro valor no es compatible, por tanto, su comportamiento sin definir.  
  
 **vtReturn**  
 El tipo variant de la función de valor devuelto.  
  
 **nParams**  
 El número de parámetros de función.  
  
 **pVarTypes**  
 Una matriz de tipos de variante de los parámetros de función.  
  
## <a name="remarks"></a>Comentarios  
 Internamente, ATL utiliza esta estructura que contiene la información obtenida de una biblioteca de tipos. Puede que necesite manipular directamente esta estructura si se proporciona información de tipo de un controlador de eventos que se usa con la [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) clase y [macro SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) macro.  
  
## <a name="example"></a>Ejemplo  
 Dado un método de interfaz dispinterface definido en un IDL:  
  
 [!code-cpp[NVC_ATL_Windowing #139](../../atl/codesnippet/cpp/atl-func-info-structure_1.idl)]  
  
 tendría que definir una `_ATL_FUNC_INFO` estructura:  
  
 [!code-cpp[NVC_ATL_Windowing #140](../../atl/codesnippet/cpp/atl-func-info-structure_2.h)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras](../../atl/reference/atl-structures.md)   
 [IDispEventSimpleImpl (clase)](../../atl/reference/idispeventsimpleimpl-class.md)   
 [MACRO SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)






