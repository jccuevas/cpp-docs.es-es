---
title: Macros de Control compuesto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- composite controls, macros
ms.assetid: 17f2dd5e-07e6-4aa6-b965-7a361c78c45e
caps.latest.revision: 16
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
translationtype: Machine Translation
ms.sourcegitcommit: 8cdedc5cfac9d49df812ae6fcfcc548201b1edb5
ms.openlocfilehash: 9fb8a907c8052c9816d6b87247e903a63f34a5be
ms.lasthandoff: 02/24/2017

---
# <a name="composite-control-macros"></a>Macros de Control compuesto
Estas macros definen entradas y mapas de receptor de eventos.  
  
|||  
|-|-|  
|[BEGIN_SINK_MAP](#begin_sink_map)|Marca el comienzo de la asignación de receptor de eventos para el control compuesto.|  
|[END_SINK_MAP](#end_sink_map)|Marca el final de la asignación de receptor de eventos para el control compuesto.|  
|[SINK_ENTRY](#sink_entry)|Entrada en el mapa de receptores de eventos.|  
|[SINK_ENTRY_EX](#sink_entry_ex)|Entrada en el mapa de receptores de eventos con un parámetro adicional.| 
|[SINK_ENTRY_EX_P](#sink_entry_ex)| (2017 de visual Studio) Similar a SINK_ENTRY_EX, excepto que toma un puntero a iid.|  
|[MACRO SINK_ENTRY_INFO](#sink_entry_info)|Entrada al mapa de receptores de eventos con información de tipo proporcionado manualmente para su uso con [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md).|  
|[SINK_ENTRY_INFO_P](#sink_entry_info)| (2017 de visual Studio) Similar a la macro SINK_ENTRY_INFO, excepto que toma un puntero a iid.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  

##  <a name="a-namebeginsinkmapa--beginsinkmap"></a><a name="begin_sink_map"></a>BEGIN_SINK_MAP  
 Declara el comienzo de la asignación de receptor de eventos para el control compuesto.  
  
```
BEGIN_SINK_MAP(_class)
```  
  
### <a name="parameters"></a>Parámetros  
 `_class`  
 [in] Especifica el control.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#104;](../../atl/codesnippet/cpp/composite-control-macros_1.h)]  
  
### <a name="remarks"></a>Comentarios  
 Implementación de ATL CE de ActiveX eventos receptores solo admite valores devueltos de tipo HRESULT o void desde los métodos de controlador de eventos; no se admite ningún otro tipo de valor devuelto y su comportamiento es indefinido.  
  
##  <a name="a-nameendsinkmapa--endsinkmap"></a><a name="end_sink_map"></a>END_SINK_MAP  
 Declara el final de la asignación de receptor de eventos para el control compuesto.  
  
```
END_SINK_MAP()
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#104;](../../atl/codesnippet/cpp/composite-control-macros_1.h)]  
  
### <a name="remarks"></a>Comentarios  
 Implementación de ATL CE de ActiveX eventos receptores solo admite valores devueltos de tipo HRESULT o void desde los métodos de controlador de eventos; no se admite ningún otro tipo de valor devuelto y su comportamiento es indefinido.  
  
##  <a name="a-namesinkentrya--sinkentry"></a><a name="sink_entry"></a>SINK_ENTRY  
 Declara la función de controlador ( `fn`) para el evento especificado ( `dispid`), del control identificado por `id`.  
  
```
SINK_ENTRY( id, dispid, fn )
```  
  
### <a name="parameters"></a>Parámetros  
 `id`  
 [in] Identifica el control.  
  
 `dispid`  
 [in] Identifica el evento especificado.  
  
 `fn`  
 [in] Nombre de la función de controlador de eventos. Esta función se debe utilizar el **_stdcall** convención de llamada y tienen la firma de estilo de dispinterface adecuado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#104;](../../atl/codesnippet/cpp/composite-control-macros_1.h)]  
  
### <a name="remarks"></a>Comentarios  
 Implementación de ATL CE de ActiveX eventos receptores solo admite valores devueltos de tipo HRESULT o void desde los métodos de controlador de eventos; no se admite ningún otro tipo de valor devuelto y su comportamiento es indefinido.  
  
##  <a name="a-namesinkentryexa--sinkentryex-and-sinkentryexp"></a><a name="sink_entry_ex"></a>SINK_ENTRY_EX y SINK_ENTRY_EX_P
 Declara la función de controlador ( `fn`) para el evento especificado ( `dispid`), la interfaz de envío ( *iid)*, para el control identificado por `id`.  
  
```
SINK_ENTRY_EX( id, iid, dispid, fn )
SINK_ENTRY_EX_P( id, piid, dispid, fn ) // (Visual Studio 2017)
```  
  
### <a name="parameters"></a>Parámetros  
 `id`  
 [in] Identifica el control.  
  
 `iid`  
 [in] Identifica la interfaz de envío.  

 `piid`  
 [in] Puntero a la interfaz de envío.  
  
 `dispid`  
 [in] Identifica el evento especificado.  
  
 `fn`  
 [in] Nombre de la función de controlador de eventos. Esta función se debe utilizar el **_stdcall** convención de llamada y tienen la firma de estilo de dispinterface adecuado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#136;](../../atl/codesnippet/cpp/composite-control-macros_2.h)]  
  
### <a name="remarks"></a>Comentarios  
 Implementación de ATL CE de ActiveX eventos receptores solo admite valores devueltos de tipo HRESULT o void desde los métodos de controlador de eventos; no se admite ningún otro tipo de valor devuelto y su comportamiento es indefinido.  
  
##  <a name="a-namesinkentryinfoa--sinkentryinfo-and-sinkentryinfop"></a><a name="sink_entry_info"></a>Macro SINK_ENTRY_INFO y SINK_ENTRY_INFO_P  
 Utilice la `SINK_ENTRY_INFO` macro dentro de un mapa de receptores de eventos para proporcionar la información necesaria para [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) enrutar eventos a la función de controlador correspondiente.  
  
```
SINK_ENTRY_INFO( id, iid, dispid, fn, info )
SINK_ENTRY_INFO_P( id, piid, dispid, fn, info ) // (Visual Studio 2017)
```  
  
### <a name="parameters"></a>Parámetros  
 `id`  
 [in] Entero sin signo que identifica el origen del evento. Este valor debe coincidir con el `nID` parámetro de plantilla que se usa en relacionado [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) clase base.  
  
 `iid`  
 [in] IID que identifica la interfaz de envío.  

 `piid`  
 [in] Puntero a IID que identifica la interfaz de envío.
  
 `dispid`  
 [in] DISPID identifica el evento especificado.  
  
 `fn`  
 [in] Nombre de la función de controlador de eventos. Esta función se debe utilizar el **_stdcall** convención de llamada y tienen la firma de estilo de dispinterface adecuado.  
  
 `info`  
 [in] Escriba la información de la función de controlador de eventos. Esta información de tipo se proporciona en forma de un puntero a un `_ATL_FUNC_INFO` estructura. `CC_CDECL`es la única opción admitida de Windows CE para la `CALLCONV` campo de la `_ATL_FUNC_INFO` estructura. Cualquier otro valor no es compatible, por tanto, su comportamiento sin definir.  
  
### <a name="remarks"></a>Comentarios  
 Los parámetros de cuatro primeros macro son los mismos que los de la [SINK_ENTRY_EX](#sink_entry_ex) (macro). El parámetro final proporciona información de tipo de evento. Implementación de ATL CE de ActiveX eventos receptores solo admite valores devueltos de tipo HRESULT o void desde los métodos de controlador de eventos; no se admite ningún otro tipo de valor devuelto y su comportamiento es indefinido.  
  

## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)   
 [Funciones globales de controles compuestos](../../atl/reference/composite-control-global-functions.md)

