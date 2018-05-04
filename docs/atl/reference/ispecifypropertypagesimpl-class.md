---
title: Clase de ISpecifyPropertyPagesImpl | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl::GetPages
dev_langs:
- C++
helpviewer_keywords:
- property pages, CLSIDs associated with
- ISpecifyPropertyPages
- ISpecifyPropertyPagesImpl class
ms.assetid: 4e4b9795-b656-4d56-9b8c-85941e7731f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74f10684c32cc5b1b4b07ac30406520c9ba41ddd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="ispecifypropertypagesimpl-class"></a>Clase de ISpecifyPropertyPagesImpl
Esta clase implementa **IUnknown** y proporciona una implementación predeterminada de la [ISpecifyPropertyPages](http://msdn.microsoft.com/library/windows/desktop/ms695217) interfaz.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T>  
class ATL_NO_VTABLE ISpecifyPropertyPagesImpl 
   : public ISpecifyPropertyPages
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `ISpecifyPropertyPagesImpl`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ISpecifyPropertyPagesImpl::GetPages](#getpages)|Rellena los valores de matriz de recuento de UUID. Cada UUID se corresponde con el CLSID de uno de las páginas de propiedades que se pueden mostrar en la hoja de propiedades del objeto.|  
  
## <a name="remarks"></a>Comentarios  
 El [ISpecifyPropertyPages](http://msdn.microsoft.com/library/windows/desktop/ms695217) interfaz permite que un cliente obtener una lista de CLSID para las páginas de propiedades admitidos por un objeto. Clase `ISpecifyPropertyPagesImpl` proporciona una implementación predeterminada de esta interfaz e implementa **IUnknown** mediante el envío de información para el volcado de memoria compilaciones dispositivo en versiones de depuración.  
  
> [!NOTE]
>  No exponga el **ISpecifyPropertyPages** si el objeto no admite páginas de propiedades de la interfaz.  
  
 **Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ISpecifyPropertyPages`  
  
 `ISpecifyPropertyPagesImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="getpages"></a>  ISpecifyPropertyPagesImpl::GetPages  
 Rellena la matriz la [CAUUID](http://msdn.microsoft.com/library/windows/desktop/ms680048) estructura con el CLSID para las páginas de propiedades que se pueden mostrar en la hoja de propiedades del objeto.  
  
```
STDMETHOD(GetPages)(CAUUID* pPages);
```  
  
### <a name="remarks"></a>Comentarios  
 ATL usa asignación de propiedad del objeto para recuperar cada CLSID.  
  
 Vea [ISpecifyPropertyPages::GetPages](http://msdn.microsoft.com/library/windows/desktop/ms687276) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [IPropertyPageImpl (clase)](../../atl/reference/ipropertypageimpl-class.md)   
 [Clase IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
