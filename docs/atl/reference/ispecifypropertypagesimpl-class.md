---
title: Clase de ISpecifyPropertyPagesImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 20
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 4d5f74de2ec6569527221cf94df6f7921f4bb4c9
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="ispecifypropertypagesimpl-class"></a>Clase de ISpecifyPropertyPagesImpl
Esta clase implementa **IUnknown** y proporciona una implementación predeterminada de la [ISpecifyPropertyPages](http://msdn.microsoft.com/library/windows/desktop/ms695217) interfaz.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
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
  
|Nombre|Descripción|  
|----------|-----------------|  
|[ISpecifyPropertyPagesImpl::GetPages](#getpages)|Rellena los valores de matriz de recuento de UUID. Cada UUID se corresponde con el CLSID de una de las páginas de propiedades que se pueden mostrar en la hoja de propiedades del objeto.|  
  
## <a name="remarks"></a>Comentarios  
 El [ISpecifyPropertyPages](http://msdn.microsoft.com/library/windows/desktop/ms695217) interfaz permite que un cliente obtener una lista de CLSID para las páginas de propiedades admitidos por un objeto. Clase `ISpecifyPropertyPagesImpl` proporciona una implementación predeterminada de esta interfaz e implementa **IUnknown** mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.  
  
> [!NOTE]
>  No exponga el **ISpecifyPropertyPages** si el objeto no admite páginas de propiedades de la interfaz.  
  
 **Artículos relacionados con** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ISpecifyPropertyPages`  
  
 `ISpecifyPropertyPagesImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="getpages"></a>ISpecifyPropertyPagesImpl::GetPages  
 Rellena la matriz la [CAUUID](http://msdn.microsoft.com/library/windows/desktop/ms680048) estructura con el CLSID para las páginas de propiedades que se pueden mostrar en la hoja de propiedades del objeto.  
  
```
STDMETHOD(GetPages)(CAUUID* pPages);
```  
  
### <a name="remarks"></a>Comentarios  
 ATL utiliza la asignación de propiedad del objeto para recuperar cada CLSID.  
  
 Consulte [ISpecifyPropertyPages::GetPages](http://msdn.microsoft.com/library/windows/desktop/ms687276) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [IPropertyPageImpl (clase)](../../atl/reference/ipropertypageimpl-class.md)   
 [Clase IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

