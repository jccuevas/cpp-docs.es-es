---
title: Clase IPropertyPage2Impl | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl::EditProperty
dev_langs:
- C++
helpviewer_keywords:
- property pages
- IPropertyPage2 ATL implementation
- IPropertyPage2Impl class
ms.assetid: e89fbe90-203a-47f0-a5de-23616697e1ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 204f62e667bd149dd174f960ba31d8388e01394e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361907"
---
# <a name="ipropertypage2impl-class"></a>Clase IPropertyPage2Impl
Esta clase implementa **IUnknown** y hereda de la implementación predeterminada de [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md).  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T>  
class IPropertyPage2Impl : public IPropertyPageImpl<T>
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `IPropertyPage2Impl`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IPropertyPage2Impl::EditProperty](#editproperty)|Especifica qué control de propiedad recibirá el foco cuando se activa la página de propiedades. Devuelve la implementación de ATL **E_NOTIMPL**.|  
  
## <a name="remarks"></a>Comentarios  
 El [IPropertyPage2](http://msdn.microsoft.com/library/windows/desktop/ms683996) interfaz extiende [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) agregando el `EditProperty` método. Este método permite que un cliente seleccionar una propiedad específica en un objeto de página de propiedades.  
  
 Clase `IPropertyPage2Impl` simplemente devuelve **E_NOTIMPL** para **IPropertyPage2::EditProperty**. Sin embargo, hereda de la implementación predeterminada de [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md) e implementa **IUnknown** mediante el envío de información para el volcado de memoria compilaciones dispositivo en versiones de depuración.  
  
 Cuando se crea una página de propiedades, la clase se deriva normalmente de `IPropertyPageImpl`. Para proporcionar la compatibilidad adicional de **IPropertyPage2**, modifique la definición de clase e invalidar el `EditProperty` método.  
  
 **Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IPropertyPage`  
  
 [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)  
  
 `IPropertyPage2Impl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
##  <a name="editproperty"></a>  IPropertyPage2Impl::EditProperty  
 Especifica qué control de propiedad recibirá el foco cuando se activa la página de propiedades.  
  
```
HRESULT EditProperty(DISPID dispID);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **E_NOTIMPL**.  
  
### <a name="remarks"></a>Comentarios  
 Vea [IPropertyPage2::EditProperty](http://msdn.microsoft.com/library/windows/desktop/ms690353) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Clase IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [Clase de ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
