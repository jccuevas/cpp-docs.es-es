---
title: Clase IPersistPropertyBagImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl::GetClassID
- ATLCOM/ATL::IPersistPropertyBagImpl::InitNew
- ATLCOM/ATL::IPersistPropertyBagImpl::Load
- ATLCOM/ATL::IPersistPropertyBagImpl::Save
dev_langs: C++
helpviewer_keywords: IPersistPropertyBagImpl class
ms.assetid: 712af24d-99f8-40f2-9811-53b3ff6e5b19
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1854f4c078bb6c8ce6a987961dc75444e104278c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="ipersistpropertybagimpl-class"></a>Clase IPersistPropertyBagImpl
Esta clase implementa **IUnknown** y permite que un objeto guardar sus propiedades en una bolsa de propiedades proporcionado por el cliente.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T>  
class ATL_NO_VTABLE IPersistPropertyBagImpl : public IPersistPropertyBag
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `IPersistPropertyBagImpl`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IPersistPropertyBagImpl::GetClassID](#getclassid)|Recupera el CLSID del objeto.|  
|[IPersistPropertyBagImpl::InitNew](#initnew)|Inicializa un objeto recién creado. Devuelve la implementación de ATL `S_OK`.|  
|[IPersistPropertyBagImpl::Load](#load)|Carga las propiedades del objeto de un contenedor de propiedades proporcionado por el cliente.|  
|[IPersistPropertyBagImpl::Save](#save)|Guarda las propiedades del objeto en una bolsa de propiedades proporcionado por el cliente.|  
  
## <a name="remarks"></a>Comentarios  
 El [IPersistPropertyBag](https://msdn.microsoft.com/library/aa768205.aspx) interfaz permite que un objeto guardar sus propiedades en una bolsa de propiedades proporcionado por el cliente. Clase `IPersistPropertyBagImpl` proporciona una implementación predeterminada de esta interfaz e implementa **IUnknown** mediante el envío de información para el volcado de memoria compilaciones dispositivo en versiones de depuración.  
  
 **IPersistPropertyBag** funciona junto con [IPropertyBag](https://msdn.microsoft.com/library/aa768196.aspx) y [IErrorLog](https://msdn.microsoft.com/library/aa768231.aspx). Estas dos interfaces de este últimas deben implementarse mediante el cliente. A través de `IPropertyBag`, el cliente guarda y carga las propiedades del objeto individuales. A través de **IErrorLog**, el objeto y el cliente pueden notificar los errores detectados.  
  
 **Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IPersistPropertyBag`  
  
 `IPersistPropertyBagImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="getclassid"></a>IPersistPropertyBagImpl::GetClassID  
 Recupera el CLSID del objeto.  
  
```
STDMETHOD(GetClassID)(CLSID* pClassID);
```  
  
### <a name="remarks"></a>Comentarios  
 Vea [IPersist:: GetClassID](http://msdn.microsoft.com/library/windows/desktop/ms688664) en el SDK de Windows.  
  
##  <a name="initnew"></a>IPersistPropertyBagImpl::InitNew  
 Inicializa un objeto recién creado.  
  
```
STDMETHOD(InitNew)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Vea [IPersistPropertyBag::InitNew](https://msdn.microsoft.com/library/aa768204.aspx) en el SDK de Windows.  
  
##  <a name="load"></a>IPersistPropertyBagImpl::Load  
 Carga las propiedades del objeto de un contenedor de propiedades proporcionado por el cliente.  
  
```
STDMETHOD(Load)(LPPROPERTYBAG pPropBag, LPERRORLOG pErrorLog);
```  
  
### <a name="remarks"></a>Comentarios  
 ATL usa asignación de propiedad del objeto para recuperar esta información.  
  
 Vea [IPersistPropertyBag](https://msdn.microsoft.com/library/aa768206.aspx) en el SDK de Windows.  
  
##  <a name="save"></a>IPersistPropertyBagImpl::Save  
 Guarda las propiedades del objeto en una bolsa de propiedades proporcionado por el cliente.  
  
```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```  
  
### <a name="remarks"></a>Comentarios  
 ATL usa asignación de propiedad del objeto para almacenar esta información. De forma predeterminada, este método guarda todas las propiedades, independientemente del valor de *fSaveAllProperties*.  
  
 Vea [IPersistPropertyBag::Save](https://msdn.microsoft.com/library/aa768207.aspx) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [BEGIN_PROP_MAP](property-map-macros.md#begin_prop_map)   
 [Información general de clases](../../atl/atl-class-overview.md)
