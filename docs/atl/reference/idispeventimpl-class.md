---
title: IDispEventImpl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
caps.latest.revision: 22
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 235955f8573ae7e430be3de2a96efdd7496d15de
ms.lasthandoff: 02/24/2017

---
# <a name="idispeventimpl-class"></a>IDispEventImpl (clase)
Esta clase proporciona las implementaciones de la `IDispatch` métodos.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
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
 `nID`  
 Un identificador único para el objeto de origen. Cuando `IDispEventImpl` es la clase base para un control compuesto, utilice el identificador de recurso del control contenido deseado para este parámetro. En otros casos, utilice un entero positivo arbitrario.  
  
 `T`  
 Clase de usuario, que se deriva de `IDispEventImpl`.  
  
 `pdiid`  
 Puntero para el IID de la interfaz de evento dispinterface implementada por esta clase. Esta interfaz se debe definir en la biblioteca de tipos denotada por `plibid`, `wMajor`, y `wMinor`.  
  
 `plibid`  
 Señala un puntero a la biblioteca de tipos que define la interfaz de envío `pdiid`. Si **aspecto GUID_NULL**, la biblioteca de tipos se cargará desde el objeto que origina los eventos.  
  
 `wMajor`  
 La versión principal de la biblioteca de tipos. El valor predeterminado es 0.  
  
 `wMinor`  
 La versión secundaria de la biblioteca de tipos. El valor predeterminado es 0.  
  
 `tihclass`  
 La clase que se utiliza para administrar la información de tipo `T`. El valor predeterminado es una clase de tipo `CComTypeInfoHolder`; sin embargo, puede invalidar este parámetro de plantilla proporcionando una clase de un tipo distinto de `CComTypeInfoHolder`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IDispEventImpl::_tihclass](../../atl/reference/idispeventimpl-class.md)|La clase utilizada para administrar la información de tipo. De forma predeterminada, `CComTypeInfoHolder`.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IDispEventImpl::IDispEventImpl](#idispeventimpl)|El constructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IDispEventImpl::GetFuncInfoFromId](#getfuncinfofromid)|Busca el índice de la función para el identificador de envío especificado.|  
|[IDispEventImpl::GetIDsOfNames](#getidsofnames)|Un solo miembro y un conjunto opcional de nombres de argumento se asigna a un conjunto correspondiente de identificadores DispId de entero.|  
|[IDispEventImpl::GetTypeInfo](#gettypeinfo)|Recupera la información de tipo para un objeto.|  
|[IDispEventImpl::GetTypeInfoCount](#gettypeinfocount)|Recupera el número de interfaces de información de tipo.|  
|[IDispEventImpl::GetUserDefinedType](#getuserdefinedtype)|Recupera el tipo básico de un tipo definido por el usuario.|  
  
## <a name="remarks"></a>Comentarios  
 `IDispEventImpl`Proporciona una manera de implementar una interfaz dispinterface de eventos sin necesidad de proporcionar código de implementación para cada método o evento de esa interfaz. `IDispEventImpl`proporciona implementaciones de la `IDispatch` métodos. Solo debe proporcionar implementaciones para los que está interesado en el control de eventos.  
  
 `IDispEventImpl`funciona junto con el [mapa de receptores de eventos](http://msdn.microsoft.com/library/32542b3d-ac43-4139-8ac4-41c48481744f) en la clase enrutar eventos a la función de controlador adecuado. Para utilizar esta clase:  
  

 Agregar un [SINK_ENTRY](http://msdn.microsoft.com/library/33a5fff6-5248-47c0-8cf4-8bdf760e86e5) o [SINK_ENTRY_EX](http://msdn.microsoft.com/library/e1d14342-838f-4791-ac2f-5dae2801c1ac) macro al mapa de receptores de eventos para cada evento en cada objeto que desea administrar. Al usar `IDispEventImpl` como una clase base de un control compuesto, se puede llamar a [AtlAdviseSinkMap](http://msdn.microsoft.com/library/0757a6af-3de3-4179-8b4f-ccd137d919b4) para establecer e interrumpir la conexión con los orígenes de eventos para todas las entradas de mapa de receptores de eventos. En otros casos, o para un mayor control, llame a [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) para establecer la conexión entre el objeto de origen y la clase base. Llame a [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise) para interrumpir la conexión.  

  
 Debe derivar de `IDispEventImpl` (con un valor único para `nID`) para cada objeto para el que necesite controlar eventos. Puede volver a usar la clase base por desaconsejar con objeto de un origen aconsejar a continuación, en el objeto de origen diferente, pero el número máximo de objetos de origen que pueden administrarse mediante un único objeto en un momento dado está limitado por el número de `IDispEventImpl` clases base.  
  
 `IDispEventImpl`proporciona la misma funcionalidad que [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md), salvo que obtiene información de tipo sobre la interfaz de una biblioteca de tipos en lugar de tener que suministrados como un puntero a un [estructuras _ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) estructura. Utilice `IDispEventSimpleImpl` cuando no tiene una biblioteca de tipos que describe la interfaz de eventos o para evitar la sobrecarga asociada al uso de la biblioteca de tipos.  
  
> [!NOTE]
> `IDispEventImpl`y `IDispEventSimpleImpl` proporcionar su propia implementación de **IUnknown:: QueryInterface** habilitar cada `IDispEventImpl` y `IDispEventSimpleImpl` clase base para actuar como una identidad de COM independiente mientras sigue permitiendo el acceso directo a los miembros de clase en el objeto COM principal.  
  
 Implementación de ATL CE de ActiveX eventos receptores solo admite valores devueltos de tipo HRESULT o void desde los métodos de controlador de eventos; no se admite ningún otro tipo de valor devuelto y su comportamiento es indefinido.  
  
 Para obtener más información, consulte [admitir IDispEventImpl](../../atl/supporting-idispeventimpl.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `_IDispEvent`  
  
 `_IDispEventLocator`  
  
 [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)  
  
 `IDispEventImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="getfuncinfofromid"></a>IDispEventImpl::GetFuncInfoFromId  
 Busca el índice de la función para el identificador de envío especificado.  
  
```
HRESULT GetFuncInfoFromId(
    const IID& iid,
    DISPID dispidMember,
    LCID lcid,
    _ATL_FUNC_INFO& info);
```  
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 [in] Una referencia al identificador de la función.  
  
 *dispidMember*  
 [in] El identificador de envío de la función.  
  
 `lcid`  
 [in] El contexto de la configuración regional del identificador de función.  
  
 `info`  
 [in] La estructura que indica cómo se llama a la función.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
##  <a name="getidsofnames"></a>IDispEventImpl::GetIDsOfNames  
 Un solo miembro y un conjunto opcional de nombres de argumento se asigna a un conjunto correspondiente de entero DISPID, que se puede utilizar en llamadas posteriores a [IDispatch:: Invoke](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d).  
  
```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IDispatch:: GetIDsOfNames](http://msdn.microsoft.com/en-us/6f6cf233-3481-436e-8d6a-51f93bf91619) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="gettypeinfo"></a>IDispEventImpl::GetTypeInfo  
 Recupera la información de tipo de un objeto, que se puede usar después para obtener la información de tipo de una interfaz.  
  
```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="gettypeinfocount"></a>IDispEventImpl::GetTypeInfoCount  
 Recupera el número de interfaces de información de tipo que proporciona un objeto (0 ó 1).  
  
```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IDispatch:: GetTypeInfoCount](http://msdn.microsoft.com/en-us/da876d53-cb8a-465c-a43e-c0eb272e2a12) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getuserdefinedtype"></a>IDispEventImpl::GetUserDefinedType  
 Recupera el tipo básico de un tipo definido por el usuario.  
  
```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```  
  
### <a name="parameters"></a>Parámetros  
 `pTI`  
 [in] Un puntero a la [ITypeInfo](http://msdn.microsoft.com/en-us/f3356463-3373-4279-bae1-953378aa2680) interfaz que contiene el tipo definido por el usuario.  
  
 *HRT*  
 [in] Identificador de la descripción del tipo que se va a recuperar.  
  
### <a name="return-value"></a>Valor devuelto  
 El tipo de variante.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [ITypeInfo:: GetRefTypeInfo](http://msdn.microsoft.com/en-us/61d3b31d-6591-4e55-9e82-5246a168be00).  
  
##  <a name="idispeventimpl"></a>IDispEventImpl::IDispEventImpl  
 El constructor. Almacena los valores de los parámetros de plantilla de clase `plibid`, `pdiid`, `wMajor`, y `wMinor`.  
  
```
IDispEventImpl();
```  
  
##  <a name="tihclass"></a>IDispEventImpl::tihclass  
 Esta definición de tipo es una instancia del parámetro de plantilla de clase `tihclass`.  
  
```
typedef tihclass _tihclass;
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, es la clase `CComTypeInfoHolder`. `CComTypeInfoHolder`administra la información de tipo para la clase.  
  
## <a name="see-also"></a>Vea también  
 [Estructura de estructuras _ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)   
 [IDispatchImpl (clase)](../../atl/reference/idispatchimpl-class.md)   
 [IDispEventSimpleImpl (clase)](../../atl/reference/idispeventsimpleimpl-class.md)   
 [SINK_ENTRY](http://msdn.microsoft.com/library/33a5fff6-5248-47c0-8cf4-8bdf760e86e5)   
 [SINK_ENTRY_EX](http://msdn.microsoft.com/library/e1d14342-838f-4791-ac2f-5dae2801c1ac)   
 [MACRO SINK_ENTRY_INFO](http://msdn.microsoft.com/library/1a0ae260-2c82-4926-a537-db01e5f206a7)   
 [Información general de la clase](../../atl/atl-class-overview.md)
