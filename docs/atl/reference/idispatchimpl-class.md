---
title: IDispatchImpl (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IDispatchImpl
- ATLCOM/ATL::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::GetIDsOfNames
- ATLCOM/ATL::IDispatchImpl::GetTypeInfo
- ATLCOM/ATL::IDispatchImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispatchImpl::Invoke
dev_langs:
- C++
helpviewer_keywords:
- dual interfaces, classes
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 8108eb36-1228-4127-a203-3ab5ba488892
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7fddf556eba07264f6ea0b01edea3e3d1e8a3a7b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364371"
---
# <a name="idispatchimpl-class"></a>IDispatchImpl (clase)
Proporciona una implementación predeterminada para el `IDispatch` forma parte de una interfaz dual.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
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
 Un puntero a lo IID de `T`.  
  
 [in] `plibid`  
 Un puntero a LIBID de la biblioteca de tipos que contiene información acerca de la interfaz. De forma predeterminada, se pasa la biblioteca de tipos de nivel de servidor.  
  
 [in] `wMajor`  
 La versión principal de la biblioteca de tipos. De forma predeterminada, el valor es 1.  
  
 [in] `wMinor`  
 La versión secundaria de la biblioteca de tipos. De forma predeterminada, el valor es 0.  
  
 [in] `tihclass`  
 La clase que se usa para administrar la información de tipo para `T`. De forma predeterminada, el valor es `CComTypeInfoHolder`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IDispatchImpl::IDispatchImpl](#idispatchimpl)|El constructor. Llamadas `AddRef` en la variable de miembro protegido que administra la información de tipo de interfaz dual. El destructor llama a `Release`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IDispatchImpl::GetIDsOfNames](#getidsofnames)|Asigna un conjunto de nombres a un conjunto correspondiente de identificadores de envío.|  
|[IDispatchImpl::GetTypeInfo](#gettypeinfo)|Recupera la información de tipo de interfaz dual.|  
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|Determina si hay información de tipo para la interfaz dual.|  
|[IDispatchImpl::Invoke](#invoke)|Proporciona acceso a los métodos y propiedades expuestas por la interfaz dual.|  
  
## <a name="remarks"></a>Comentarios  
 `IDispatchImpl` Proporciona una implementación predeterminada para el `IDispatch` forma parte de cualquier interfaz dual en un objeto. Una interfaz dual se deriva de `IDispatch` y utiliza únicamente los tipos compatibles con la automatización. Al igual que una interfaz dispinterface, una interfaz dual admite el enlace anticipado y el enlace de tiempo de ejecución; Sin embargo, una interfaz dual también admite el enlace de vtable.  
  
 En el ejemplo siguiente se muestra una implementación típica de `IDispatchImpl`.  
  
 [!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]  
  
 De forma predeterminada, el `IDispatchImpl` busca la información de tipo de clase `T` en el registro. Para implementar una interfaz no registrada, puede usar el `IDispatchImpl` clase sin tener acceso al registro mediante el uso de un número de versión predefinidas. Si crea un `IDispatchImpl` objeto cuya 0xFFFF como el valor de `wMajor` y 0xFFFF como el valor de `wMinor`, la `IDispatchImpl` clase recupera la biblioteca de tipos desde el archivo .dll en lugar del registro.  
  
 `IDispatchImpl` contiene un miembro estático del tipo `CComTypeInfoHolder` que administra la información de tipo de interfaz dual. Si tiene varios objetos que implementan la misma dual interfaz, solo una instancia de `CComTypeInfoHolder` se utiliza.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `T`  
  
 `IDispatchImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="getidsofnames"></a>  IDispatchImpl::GetIDsOfNames  
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
 Vea [IDispatch:: GetIDsOfNames](http://msdn.microsoft.com/en-us/6f6cf233-3481-436e-8d6a-51f93bf91619) en el SDK de Windows.  
  
##  <a name="gettypeinfo"></a>  IDispatchImpl::GetTypeInfo  
 Recupera la información de tipo de interfaz dual.  
  
```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```  
  
### <a name="remarks"></a>Comentarios  
 Vea [IDispatch:: GetTypeInfo](http://msdn.microsoft.com/en-us/cc1ec9aa-6c40-4e70-819c-a7c6dd6b8c99) en el SDK de Windows.  
  
##  <a name="gettypeinfocount"></a>  IDispatchImpl::GetTypeInfoCount  
 Determina si hay información de tipo para la interfaz dual.  
  
```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```  
  
### <a name="remarks"></a>Comentarios  
 Vea `IDispatch::GetTypeInfoCount` en el SDK de Windows.  
  
##  <a name="idispatchimpl"></a>  IDispatchImpl::IDispatchImpl  
 El constructor. Llamadas `AddRef` en la variable de miembro protegido que administra la información de tipo de interfaz dual. El destructor llama **versión**.  
  
```
IDispatchImpl();
```  
  
##  <a name="invoke"></a>  IDispatchImpl::Invoke  
 Proporciona acceso a los métodos y propiedades expuestas por la interfaz dual.  
  
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
 Vea [IDispatch:: Invoke](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)
