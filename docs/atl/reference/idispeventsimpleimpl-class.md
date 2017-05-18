---
title: Clase de IDispEventSimpleImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl::Advise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventAdvise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventUnadvise
- ATLCOM/ATL::IDispEventSimpleImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventSimpleImpl::Invoke
- ATLCOM/ATL::IDispEventSimpleImpl::Unadvise
dev_langs:
- C++
helpviewer_keywords:
- IDispEventSimpleImpl class
ms.assetid: 971d82b7-a921-47fa-a4d8-909bed377ab0
caps.latest.revision: 27
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
ms.openlocfilehash: 392e8a8d8d38b0eaacce4ab013c46476516f46f7
ms.contentlocale: es-es
ms.lasthandoff: 03/31/2017

---
# <a name="idispeventsimpleimpl-class"></a>IDispEventSimpleImpl (clase)
Esta clase proporciona las implementaciones de la `IDispatch` métodos sin obtener información de tipo de una biblioteca de tipos.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <UINT nID, class T, const IID* pdiid>  
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```    
  
#### <a name="parameters"></a>Parámetros  
 `nID`  
 Un identificador único para el objeto de origen. Cuando `IDispEventSimpleImpl` es la clase base para un control compuesto, utilice el identificador de recurso del control contenido deseado para este parámetro. En otros casos, utilice un entero positivo arbitrario.  
  
 `T`  
 Clase de usuario, que se deriva de `IDispEventSimpleImpl`.  
  
 `pdiid`  
 El puntero para el IID de la interfaz de evento dispinterface implementada por esta clase.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IDispEventSimpleImpl::Advise](#advise)|Establece una conexión con el origen de eventos de forma predeterminada.|  
|[IDispEventSimpleImpl:: DispEventAdvise](#dispeventadvise)|Establece una conexión con el origen del evento.|  
|[IDispEventSimpleImpl:: DispEventUnadvise](#dispeventunadvise)|Interrumpe la conexión con el origen del evento.|  
|[IDispEventSimpleImpl::GetIDsOfNames](#getidsofnames)|Devuelve **E_NOTIMPL**.|  
|[IDispEventSimpleImpl::GetTypeInfo](#gettypeinfo)|Devuelve **E_NOTIMPL**.|  
|[IDispEventSimpleImpl::GetTypeInfoCount](#gettypeinfocount)|Devuelve **E_NOTIMPL**.|  
|[IDispEventSimpleImpl::Invoke](#invoke)|Llamadas a los controladores de eventos en el evento aparecen mapa de receptores.|  
|[IDispEventSimpleImpl::Unadvise](#unadvise)|Interrumpe la conexión con el origen de eventos de forma predeterminada.|  
  
## <a name="remarks"></a>Comentarios  
 `IDispEventSimpleImpl`Proporciona una manera de implementar una interfaz de envío de eventos sin necesidad de proporcionar código de implementación para cada método o evento en esa interfaz. `IDispEventSimpleImpl`proporciona implementaciones de la `IDispatch` métodos. Basta con proporcionar implementaciones para los que está interesado en el control de eventos.  
  
 `IDispEventSimpleImpl`funciona junto con el mapa de receptores de eventos en la clase de eventos de ruta a la función de controlador adecuado. Para utilizar esta clase:  
  
-   Agregar un [macro SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) macro en el mapa de receptores de eventos para cada evento en todos los objetos que desea administrar.  
  
-   Proporcionar información de tipo para cada evento pasando un puntero a un [estructuras _ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) estructura como un parámetro para cada entrada. En el x86 plataforma, la `_ATL_FUNC_INFO.cc` valor debe ser CC_CDECL con la función de devolución de llamada que llamar al método de __stdcall.  
  
-   Llame a [DispEventAdvise](#dispeventadvise) para establecer la conexión entre el objeto de origen y la clase base.  
  
-   Llame a [DispEventUnadvise](#dispeventunadvise) para interrumpir la conexión.  
  
 Debe derivar de `IDispEventSimpleImpl` (con un valor único para `nID`) para cada objeto para la que necesita controlar los eventos. Volver a utilizar la clase base, desaconsejar con objeto de un origen, a continuación, se avisa en un objeto de origen diferente, pero el número máximo de objetos de origen que pueda ser controlada por un único objeto al mismo tiempo está limitado por el número de `IDispEventSimpleImpl` clases base.  
  
 **IDispEventSimplImpl** proporciona la misma funcionalidad que [IDispEventImpl](../../atl/reference/idispeventimpl-class.md), excepto en que no obtiene información de tipo de la interfaz de una biblioteca de tipos. Los asistentes generan código que se basa solo en `IDispEventImpl`, pero puede usar `IDispEventSimpleImpl` agregando el código a mano. Utilice `IDispEventSimpleImpl` cuando no tiene una biblioteca de tipos que describe la interfaz de eventos o para evitar la sobrecarga asociada al uso de la biblioteca de tipos.  
  
> [!NOTE]
> `IDispEventImpl`y `IDispEventSimpleImpl` proporcionar su propia implementación de **IUnknown:: QueryInterface** habilitar cada `IDispEventImpl` o `IDispEventSimpleImpl` clase para que actúe como una identidad de COM independiente mientras sigue permitiendo el acceso directo a los miembros de clase en el objeto COM principal base.  
  
 Implementación de ATL CE de ActiveX eventos receptores solo admite valores devueltos de tipo HRESULT o void de los métodos de controlador de eventos; cualquier otro tipo de valor devuelto no es compatible y su comportamiento es indefinido.  
  
 Para obtener más información, consulte [admitir IDispEventImpl](../../atl/supporting-idispeventimpl.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `_IDispEvent`  
  
 `_IDispEventLocator`  
  
 `IDispEventSimpleImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="advise"></a>IDispEventSimpleImpl::Advise  
 Llamar a este método para establecer una conexión con el origen del evento representado por *pUnk*.  
  
```
HRESULT Advise(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>Parámetros  
 *pUnk*  
 [in] Un puntero a la **IUnknown** interfaz del objeto de origen de eventos.  
  
### <a name="return-value"></a>Valor devuelto  
 `S_OK`cualquier error o `HRESULT` valor.  
  
### <a name="remarks"></a>Comentarios  
 Una vez establecida la conexión, los eventos desencadenados desde *pUnk* se enrutará a los controladores en la clase mediante el mapa de receptores de eventos.  
  
> [!NOTE]
>  Si la clase se deriva de varios `IDispEventSimpleImpl` clases, debe eliminar la ambigüedad de llamadas a este método mediante ámbito de la llamada con la clase base concreta que le interesen.  
  
 `Advise`establece una conexión con el origen de eventos de forma predeterminada, obtiene el IID del origen del evento de manera predeterminada del objeto tal y como se determina por [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).  
  
##  <a name="dispeventadvise"></a>IDispEventSimpleImpl:: DispEventAdvise  
 Llamar a este método para establecer una conexión con el origen del evento representado por *pUnk*.  
  
```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```  
  
### <a name="parameters"></a>Parámetros  
 *pUnk*  
 [in] Un puntero a la **IUnknown** interfaz del objeto de origen de eventos.  
  
 `piid`  
 Un puntero a lo IID del objeto de origen de eventos.  
  
### <a name="return-value"></a>Valor devuelto  
 `S_OK`cualquier error o `HRESULT` valor.  
  
### <a name="remarks"></a>Comentarios  
 Posteriormente, se activan los eventos desde *pUnk* se enrutará a los controladores en la clase mediante el mapa de receptores de eventos.  
  
> [!NOTE]
>  Si la clase se deriva de varios `IDispEventSimpleImpl` clases, debe eliminar la ambigüedad de llamadas a este método mediante ámbito de la llamada con la clase base concreta que le interesen.  
  
 `DispEventAdvise`establece una conexión con el origen de eventos especificado en `pdiid`.  
  
##  <a name="dispeventunadvise"></a>IDispEventSimpleImpl:: DispEventUnadvise  
 Si se interrumpe la conexión con el origen del evento representado por *pUnk*.  
  
```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```  
  
### <a name="parameters"></a>Parámetros  
 *pUnk*  
 [in] Un puntero a la **IUnknown** interfaz del objeto de origen de eventos.  
  
 `piid`  
 Un puntero a lo IID del objeto de origen de eventos.  
  
### <a name="return-value"></a>Valor devuelto  
 `S_OK`cualquier error o `HRESULT` valor.  
  
### <a name="remarks"></a>Comentarios  
 Una vez que la conexión se interrumpe, eventos ya no se enrutarán a las funciones de controlador enumeradas en el mapa de receptores de eventos.  
  
> [!NOTE]
>  Si la clase se deriva de varios `IDispEventSimpleImpl` clases, debe eliminar la ambigüedad de llamadas a este método mediante ámbito de la llamada con la clase base concreta que le interesen.  
  
 `DispEventAdvise`interrumpe una conexión que se ha establecido con el origen de eventos especificado en `pdiid`.  
  
##  <a name="getidsofnames"></a>IDispEventSimpleImpl::GetIDsOfNames  
 Esta implementación de **IDispatch:: GetIDsOfNames** devuelve **E_NOTIMPL**.  
  
```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```  
  
### <a name="remarks"></a>Comentarios  
 Vea [IDispatch:: GetIDsOfNames](http://msdn.microsoft.com/en-us/6f6cf233-3481-436e-8d6a-51f93bf91619) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="gettypeinfo"></a>IDispEventSimpleImpl::GetTypeInfo  
 Esta implementación de **IDispatch:: GetTypeInfo** devuelve **E_NOTIMPL**.  
  
```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```  
  
### <a name="remarks"></a>Comentarios  
 Vea [IDispatch:: GetTypeInfo](http://msdn.microsoft.com/en-us/cc1ec9aa-6c40-4e70-819c-a7c6dd6b8c99) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="gettypeinfocount"></a>IDispEventSimpleImpl::GetTypeInfoCount  
 Esta implementación de **IDispatch:: GetTypeInfoCount** devuelve **E_NOTIMPL**.  
  
```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```  
  
### <a name="remarks"></a>Comentarios  
 Vea [IDispatch:: GetTypeInfoCount](http://msdn.microsoft.com/en-us/da876d53-cb8a-465c-a43e-c0eb272e2a12) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="invoke"></a>IDispEventSimpleImpl::Invoke  
 Esta implementación de **IDispatch:: Invoke** llamadas a los controladores de eventos en el evento aparecen mapa de receptores.  
  
```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID /* riid */,
    LCID lcid,
    WORD /* wFlags */,
    DISPPARMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* /* pexcepinfo */,
    UINT* /* puArgErr */);
```  
  
### <a name="remarks"></a>Comentarios  
 Vea [IDispatch:: Invoke](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d).  
  
##  <a name="unadvise"></a>IDispEventSimpleImpl::Unadvise  
 Si se interrumpe la conexión con el origen del evento representado por *pUnk*.  
  
```
HRESULT Unadvise(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>Parámetros  
 *pUnk*  
 [in] Un puntero a la **IUnknown** interfaz del objeto de origen de eventos.  
  
### <a name="return-value"></a>Valor devuelto  
 `S_OK`cualquier error o `HRESULT` valor.  
  
### <a name="remarks"></a>Comentarios  
 Una vez que la conexión se interrumpe, eventos ya no se enrutarán a las funciones de controlador enumeradas en el mapa de receptores de eventos.  
  
> [!NOTE]
>  Si la clase se deriva de varios `IDispEventSimpleImpl` clases, debe eliminar la ambigüedad de llamadas a este método mediante ámbito de la llamada con la clase base concreta que le interesen.  
  
 `Unadvise`interrumpe una conexión que se ha establecido con el origen de evento predeterminado especificado en `pdiid`.  
  
 **Unavise** saltos de una conexión con el origen de eventos de forma predeterminada, obtiene el IID del origen del evento predeterminado del objeto tal y como se determina por [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).  
  
## <a name="see-also"></a>Vea también  
 [Estructura de estructuras _ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)   
 [IDispatchImpl (clase)](../../atl/reference/idispatchimpl-class.md)   
 [IDispEventImpl (clase)](../../atl/reference/idispeventimpl-class.md)   
 [MACRO SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)   
 [Información general de clases](../../atl/atl-class-overview.md)

