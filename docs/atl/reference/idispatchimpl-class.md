---
title: Clase de IDispatchImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDispatchImpl
- ATL.IDispatchImpl
- ATL::IDispatchImpl
dev_langs:
- C++
helpviewer_keywords:
- dual interfaces, classes
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 8108eb36-1228-4127-a203-3ab5ba488892
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
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: fff4cbc0a3f87b584f1a4211f4aad37228ed4da7
ms.lasthandoff: 02/24/2017

---
# <a name="idispatchimpl-class"></a>IDispatchImpl (clase)
Proporciona una implementación predeterminada para el `IDispatch` parte de una interfaz dual.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T,
        const IID* piid= &__uuidof(T),
        const GUID* plibid = &CAtlModule::m_libid,
        WORD wMajor = 1,
        WORD wMinor = 0, 
        class tihclass = CComTypeInfoHolder>
class ATL_NO_VTABLE IDispatchImpl : public T
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `T`  
 Una interfaz dual.  
  
 [in] `piid`  
 Un puntero para el IID de `T`.  
  
 [in] `plibid`  
 Puntero a LIBID de la biblioteca de tipos que contiene información acerca de la interfaz. De forma predeterminada, se pasa la biblioteca de tipos de nivel de servidor.  
  
 [in] `wMajor`  
 La versión principal de la biblioteca de tipos. De forma predeterminada, el valor es 1.  
  
 [in] `wMinor`  
 La versión secundaria de la biblioteca de tipos. De forma predeterminada, el valor es 0.  
  
 [in] `tihclass`  
 La clase que se utiliza para administrar la información de tipo `T`. De forma predeterminada, el valor es `CComTypeInfoHolder`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IDispatchImpl::IDispatchImpl](#idispatchimpl)|El constructor. Llamadas `AddRef` en la variable de miembro protegido que administra la información de tipo de la interfaz dual. El destructor llama a `Release`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IDispatchImpl::GetIDsOfNames](#getidsofnames)|Asigna un conjunto de nombres a un conjunto correspondiente de identificadores de envío.|  
|[IDispatchImpl::GetTypeInfo](#gettypeinfo)|Recupera la información de tipo para la interfaz dual.|  
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|Determina si hay información de tipo para la interfaz dual.|  
|[IDispatchImpl::Invoke](#invoke)|Proporciona acceso a los métodos y propiedades expuestos por la interfaz dual.|  
  
## <a name="remarks"></a>Comentarios  
 `IDispatchImpl`Proporciona una implementación predeterminada para el `IDispatch` parte de cualquier interfaz dual en un objeto. Una interfaz dual se deriva de `IDispatch` y usa sólo los tipos compatibles con la automatización. Al igual que una interfaz dispinterface, una interfaz dual admite el enlace anticipado y el enlace; Sin embargo, una interfaz dual también admite el enlace de vtable.  
  
 En el ejemplo siguiente se muestra una implementación típica de `IDispatchImpl`.  
  
 [!code-cpp[NVC_ATL_COM&#47;](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]  
  
 De forma predeterminada, el `IDispatchImpl` busca la información de tipo de clase `T` en el registro. Para implementar una interfaz no registrada, puede usar el `IDispatchImpl` clase sin acceso al registro mediante el uso de un número de versión predefinidas. Si crea un `IDispatchImpl` objeto con 0xFFFF que el valor de `wMajor` y 0xFFFF como el valor de `wMinor`, la `IDispatchImpl` clase recupera la biblioteca de tipos desde el archivo .dll en lugar del registro.  
  
 `IDispatchImpl`contiene un miembro estático del tipo `CComTypeInfoHolder` que administra la información de tipo de la interfaz dual. Si tiene varios objetos que implementan la misma dual de interfaz, sólo una instancia de `CComTypeInfoHolder` se utiliza.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `T`  
  
 `IDispatchImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="a-namegetidsofnamesa--idispatchimplgetidsofnames"></a><a name="getidsofnames"></a>IDispatchImpl::GetIDsOfNames  
 Asigna un conjunto de nombres a un conjunto correspondiente de identificadores de envío.  
  
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
  
##  <a name="a-namegettypeinfoa--idispatchimplgettypeinfo"></a><a name="gettypeinfo"></a>IDispatchImpl::GetTypeInfo  
 Recupera la información de tipo para la interfaz dual.  
  
```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IDispatch:: GetTypeInfo](http://msdn.microsoft.com/en-us/cc1ec9aa-6c40-4e70-819c-a7c6dd6b8c99) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegettypeinfocounta--idispatchimplgettypeinfocount"></a><a name="gettypeinfocount"></a>IDispatchImpl::GetTypeInfoCount  
 Determina si hay información de tipo para la interfaz dual.  
  
```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```  
  
### <a name="remarks"></a>Comentarios  
 See `IDispatch::GetTypeInfoCount` in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nameidispatchimpla--idispatchimplidispatchimpl"></a><a name="idispatchimpl"></a>IDispatchImpl::IDispatchImpl  
 El constructor. Llamadas `AddRef` en la variable de miembro protegido que administra la información de tipo de la interfaz dual. El destructor llama **versión**.  
  
```
IDispatchImpl();
```  
  
##  <a name="a-nameinvokea--idispatchimplinvoke"></a><a name="invoke"></a>IDispatchImpl::Invoke  
 Proporciona acceso a los métodos y propiedades expuestos por la interfaz dual.  
  
```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID riid,
    LCID lcid,
    WORD wFlags,
    DISPPARAMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* pexcepinfo,
    UINT* puArgErr);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IDispatch:: Invoke](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)

