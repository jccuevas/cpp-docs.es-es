---
title: IDispEventImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IDispEventImpl
- ATLCOM/ATL::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::GetFuncInfoFromId
- ATLCOM/ATL::IDispEventImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventImpl::GetUserDefinedType
dev_langs:
- C++
helpviewer_keywords:
- IDispEventImpl class
ms.assetid: a64b5288-35cb-4638-aad6-2d15b1c7cf7b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b482baa9339a50b9a124c0d68b02f60b0236984e
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963756"
---
# <a name="idispeventimpl-class"></a>IDispEventImpl (clase)
Esta clase proporciona las implementaciones de la `IDispatch` métodos.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <UINT nID, class T,
    const IID* pdiid = &IID_NULL,
    const GUID* plibid = &GUID_NULL,
    WORD wMajor = 0,
    WORD wMinor = 0, 
    class tihclass = CcomTypeInfoHolder>  
class ATL_NO_VTABLE IDispEventImpl : public IDispEventSimpleImpl<nID, T, pdiid>
```  
  
#### <a name="parameters"></a>Parámetros  
 *nID*  
 Un identificador único para el objeto de origen. Cuando `IDispEventImpl` es la clase base para un control compuesto, utilice el identificador de recurso del control contenido deseado para este parámetro. En otros casos, utilice un entero positivo.  
  
 *T*  
 La clase del usuario, que se deriva de `IDispEventImpl`.  
  
 *pdiid*  
 El puntero para el IID de la interfaz dispinterface de evento implementado por esta clase. Esta interfaz se debe definir en la biblioteca de tipos que se indica con *plibid*, *wMajor*, y *wMinor*.  
  
 *plibid*  
 Un puntero a la biblioteca de tipos que define la interfaz de envío que apunta *pdiid*. Si **& GUID_NULL**, la biblioteca de tipos se cargará desde el objeto que origina los eventos.  
  
 *wMajor*  
 La versión principal de la biblioteca de tipos. El valor predeterminado es 0.  
  
 *wMinor*  
 La versión secundaria de la biblioteca de tipos. El valor predeterminado es 0.  
  
 *tihclass*  
 La clase usada para administrar la información de tipo para *T*. El valor predeterminado es una clase de tipo `CComTypeInfoHolder`; sin embargo, puede invalidar este parámetro de plantilla, ya que proporciona una clase de un tipo distinto de `CComTypeInfoHolder`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[IDispEventImpl::_tihclass](../../atl/reference/idispeventimpl-class.md)|La clase que se usa para administrar la información de tipo. De forma predeterminada, `CComTypeInfoHolder`.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IDispEventImpl::IDispEventImpl](#idispeventimpl)|El constructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IDispEventImpl::GetFuncInfoFromId](#getfuncinfofromid)|Busca el índice de la función para el identificador de envío especificado.|  
|[IDispEventImpl::GetIDsOfNames](#getidsofnames)|Un miembro único y un conjunto opcional de nombres de argumento se asigna a un conjunto correspondiente de entero de envío (DISPID).|  
|[IDispEventImpl::GetTypeInfo](#gettypeinfo)|Recupera la información de tipo para un objeto.|  
|[IDispEventImpl::GetTypeInfoCount](#gettypeinfocount)|Recupera el número de interfaces de información de tipo.|  
|[IDispEventImpl::GetUserDefinedType](#getuserdefinedtype)|Recupera el tipo básico de un tipo definido por el usuario.|  
  
## <a name="remarks"></a>Comentarios  
 `IDispEventImpl` Proporciona una manera de implementar una interfaz dispinterface de evento sin necesidad de proporcionar código de implementación para cada método o evento en esa interfaz. `IDispEventImpl` proporciona implementaciones de la `IDispatch` métodos. Solo deberá proporcionar implementaciones para los eventos que está interesado en el control.  
  
 `IDispEventImpl` funciona junto con el mapa de receptores de eventos en la clase para enrutar eventos a la función de controlador adecuado. Para usar esta clase:  
  

 Agregar un [SINK_ENTRY](composite-control-macros.md#sink_entry) o [SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex) macro al mapa de receptores de eventos para cada evento en cada objeto que desea administrar. Cuando se usa `IDispEventImpl` como una clase base de un control compuesto, se puede llamar a [AtlAdviseSinkMap](connection-point-global-functions.md#atladvisesinkmap) para establecer e interrumpir la conexión con los orígenes de eventos para todas las entradas de mapa de receptores de eventos. En otros casos, o para un mayor control, llame a [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) para establecer la conexión entre el objeto de origen y la clase base. Llame a [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise) para interrumpir la conexión.  

  
 Debe derivar de `IDispEventImpl` (con un valor único para *nID*) para cada objeto para el que necesita controlar los eventos. Puede volver a usar la clase base por desaconsejar con objeto de un origen que avisa de, a continuación, en un objeto de origen diferente, pero el número máximo de objetos de origen que pueden controlarse mediante un único objeto al mismo tiempo está limitado por el número de `IDispEventImpl` clases base.  
  
 `IDispEventImpl` proporciona la misma funcionalidad que [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md), excepto en que obtiene información de tipo de la interfaz desde una biblioteca de tipos en lugar de tener que suministrados como un puntero a un [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) estructura. Use `IDispEventSimpleImpl` cuando no tiene una biblioteca de tipos que describe la interfaz de eventos o desea evitar la sobrecarga asociada con el uso de la biblioteca de tipos.  
  
> [!NOTE]
> `IDispEventImpl` y `IDispEventSimpleImpl` proporcionar su propia implementación de `IUnknown::QueryInterface` habilitar cada `IDispEventImpl` y `IDispEventSimpleImpl` clase para que actúe como una identidad de COM independiente mientras sigue permitiendo el acceso directo a los miembros de clase en el objeto COM principal base.  
  
 Implementación de ATL de CE de ActiveX eventos receptores solo admite valores devueltos de tipo HRESULT o void desde los métodos de controlador de eventos; no se admite ningún otro tipo de valor devuelto y su comportamiento es indefinido.  
  
 Para obtener más información, consulte [admitir IDispEventImpl](../../atl/supporting-idispeventimpl.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `_IDispEvent`  
  
 `_IDispEventLocator`  
  
 [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)  
  
 `IDispEventImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="getfuncinfofromid"></a>  IDispEventImpl::GetFuncInfoFromId  
 Busca el índice de la función para el identificador de envío especificado.  
  
```
HRESULT GetFuncInfoFromId(
    const IID& iid,
    DISPID dispidMember,
    LCID lcid,
    _ATL_FUNC_INFO& info);
```  
  
### <a name="parameters"></a>Parámetros  
 *IID*  
 [in] Una referencia al identificador de la función.  
  
 *dispidMember*  
 [in] El identificador de envío de la función.  
  
 *lcid*  
 [in] El contexto de la configuración regional del identificador de función.  
  
 *Info*  
 [in] La estructura que indica cómo se llama a la función.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
##  <a name="getidsofnames"></a>  IDispEventImpl::GetIDsOfNames  
 Un miembro único y un conjunto opcional de nombres de argumento se asigna a un conjunto correspondiente de entero de envío (DISPID), que se puede usar en las llamadas subsiguientes a [IDispatch:: Invoke](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke).  
  
```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IDispatch:: GetIDsOfNames](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-getidsofnames) en el SDK de Windows.  
  
##  <a name="gettypeinfo"></a>  IDispEventImpl::GetTypeInfo  
 Recupera la información de tipo de un objeto, que se puede usar después para obtener la información de tipo de una interfaz.  
  
```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="gettypeinfocount"></a>  IDispEventImpl::GetTypeInfoCount  
 Recupera el número de interfaces de información de tipo que proporciona un objeto (0 ó 1).  
  
```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IDispatch:: GetTypeInfoCount](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) en el SDK de Windows.  
  
##  <a name="getuserdefinedtype"></a>  IDispEventImpl::GetUserDefinedType  
 Recupera el tipo básico de un tipo definido por el usuario.  
  
```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```  
  
### <a name="parameters"></a>Parámetros  
 *PTI*  
 [in] Un puntero a la [ITypeInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interfaz que contiene el tipo definido por el usuario.  
  
 *HRT*  
 [in] Identificador de la descripción del tipo van a recuperar.  
  
### <a name="return-value"></a>Valor devuelto  
 El tipo de variante.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [ITypeInfo:: GetRefTypeInfo](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-itypeinfo-getreftypeinfo).  
  
##  <a name="idispeventimpl"></a>  IDispEventImpl::IDispEventImpl  
 El constructor. Almacena los valores de los parámetros de plantilla de clase *plibid*, *pdiid*, *wMajor*, y *wMinor*.  
  
```
IDispEventImpl();
```  
  
##  <a name="tihclass"></a>  IDispEventImpl::tihclass  
 Esta definición de tipo es una instancia del parámetro de plantilla de clase *tihclass*.  
  
```
typedef tihclass _tihclass;
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, la clase es `CComTypeInfoHolder`. `CComTypeInfoHolder` administra la información de tipo para la clase.  
  
## <a name="see-also"></a>Vea también  
 [_ATL_FUNC_INFO (estructura)](../../atl/reference/atl-func-info-structure.md)   
 [IDispatchImpl (clase)](../../atl/reference/idispatchimpl-class.md)   
 [IDispEventSimpleImpl (clase)](../../atl/reference/idispeventsimpleimpl-class.md)   
 [SINK_ENTRY](composite-control-macros.md#sink_entry)   
 [SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)   
 [MACRO SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)   
 [Información general de clases](../../atl/atl-class-overview.md)