---
title: IPerPropertyBrowsingImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetDisplayString
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedStrings
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedValue
- ATLCTL/ATL::IPerPropertyBrowsingImpl::MapPropertyToPage
dev_langs:
- C++
helpviewer_keywords:
- IPerPropertyBrowsingImpl class
- property pages, accessing information
- IPerPropertyBrowsing, ATL implementation
ms.assetid: 0b1a9be3-d242-4767-be69-663a21e4b728
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c018b5c7ffa8e72ae9ce68fb23799d712a879df8
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206681"
---
# <a name="iperpropertybrowsingimpl-class"></a>IPerPropertyBrowsingImpl (clase)
Esta clase implementa `IUnknown` y permite que un cliente tener acceso a la información de las páginas de propiedades de un objeto.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```

template <class T>
class ATL_NO_VTABLE IPerPropertyBrowsingImpl :
    public IPerPropertyBrowsing
```  
  
#### <a name="parameters"></a>Parámetros  
 *T*  
 La clase derivada de `IPerPropertyBrowsingImpl`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IPerPropertyBrowsingImpl::GetDisplayString](#getdisplaystring)|Recupera una cadena que describe una propiedad determinada.|  
|[IPerPropertyBrowsingImpl::GetPredefinedStrings](#getpredefinedstrings)|Recupera una matriz de cadenas que corresponde a los valores que una propiedad determinada puede aceptar.|  
|[IPerPropertyBrowsingImpl::GetPredefinedValue](#getpredefinedvalue)|Recupera un valor de tipo VARIANT que contiene el valor de una propiedad identificada por un DISPID determinado. El identificador de envío está asociado con el nombre de cadena que se recupera de `GetPredefinedStrings`. La implementación de ATL devuelve E_NOTIMPL.|  
|[IPerPropertyBrowsingImpl::MapPropertyToPage](#mappropertytopage)|Recupera el CLSID de la página de propiedades asociado con una propiedad determinada.|  
  
## <a name="remarks"></a>Comentarios  
 El [IPerPropertyBrowsing](/windows/desktop/api/ocidl/nn-ocidl-iperpropertybrowsing) interfaz permite que un cliente tener acceso a la información de las páginas de propiedades de un objeto. Clase `IPerPropertyBrowsingImpl` proporciona una implementación predeterminada de esta interfaz e implementa `IUnknown` mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.  
  
> [!NOTE]
>  Si utiliza Microsoft Access como la aplicación de contenedor, debe derivar la clase de `IPerPropertyBrowsingImpl`. En caso contrario, el acceso no cargará el control.  
  
 **Artículos relacionados con** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IPerPropertyBrowsing`  
  
 `IPerPropertyBrowsingImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
##  <a name="getdisplaystring"></a>  IPerPropertyBrowsingImpl::GetDisplayString  
 Recupera una cadena que describe una propiedad determinada.  
  
```
STDMETHOD(GetDisplayString)(
    DISPID dispID,
    BSTR* pBstr);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IPerPropertyBrowsing::GetDisplayString](/windows/desktop/api/ocidl/nf-ocidl-iperpropertybrowsing-getdisplaystring) en el SDK de Windows.  
  
##  <a name="getpredefinedstrings"></a>  IPerPropertyBrowsingImpl::GetPredefinedStrings  
 Llena cada matriz con cero elementos.  
  
```
STDMETHOD(GetPredefinedStrings)(
    DISPID dispID,
    CALPOLESTR* pCaStringsOut,
    CADWORD* pCaCookiesOut);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Implementación de ATL de [GetPredefinedValue](#getpredefinedvalue) devuelve E_NOTIMPL.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IPerPropertyBrowsing::](/windows/desktop/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedstrings) en el SDK de Windows.  
  
##  <a name="getpredefinedvalue"></a>  IPerPropertyBrowsingImpl::GetPredefinedValue  
 Recupera un valor de tipo VARIANT que contiene el valor de una propiedad identificada por un DISPID determinado. El identificador de envío está asociado con el nombre de cadena que se recupera de `GetPredefinedStrings`.  
  
```
STDMETHOD(GetPredefinedValue)(
    DISPID dispID,
    DWORD dwCookie,
    VARIANT* pVarOut);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve E_NOTIMPL.  
  
### <a name="remarks"></a>Comentarios  
 Implementación de ATL de [GetPredefinedStrings](#getpredefinedstrings) no recupera ningún cadenas correspondientes.  
  
 Consulte [IPerPropertyBrowsing::GetPredefinedValue](/windows/desktop/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedvalue) en el SDK de Windows.  
  
##  <a name="mappropertytopage"></a>  IPerPropertyBrowsingImpl::MapPropertyToPage  
 Recupera el CLSID de la página de propiedades asociada con la propiedad especificada.  
  
```
STDMETHOD(MapPropertyToPage)(
    DISPID dispID,
    CLSID* pClsid);
```  
  
### <a name="remarks"></a>Comentarios  
 ATL usa asignación de propiedad del objeto para obtener esta información.  
  
 Consulte [IPerPropertyBrowsing::MapPropertyToPage](/windows/desktop/api/ocidl/nf-ocidl-iperpropertybrowsing-mappropertytopage) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [IPropertyPageImpl (clase)](../../atl/reference/ipropertypageimpl-class.md)   
 [ISpecifyPropertyPagesImpl (clase)](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
