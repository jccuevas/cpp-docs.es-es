---
title: Typedefs ATL | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: 'index-page '
dev_langs:
- C++
helpviewer_keywords:
- typedefs, ATL
- typedefs
- ATL, typedefs
ms.assetid: 7dd05baa-3efb-4e3b-af23-793c610f4560
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
ms.sourcegitcommit: 347e7bf7cd9173fb2815f44fc052ec23ab4055a6
ms.openlocfilehash: aa57212b602538e4e8d2854c6075562e72472796
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="atl-typedefs"></a>Typedefs ATL
Active Template Library incluye las siguientes definiciones de tipo.  
  
|||  
|-|-|  
|[_ATL_BASE_MODULE](#_atl_base_module)|Define como un typedef basado en [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).|  
|[_ATL_COM_MODULE](#_atl_com_module)|Define como un typedef basado en [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).|  
|[_ATL_MODULE](#_atl_module)|Define como un typedef basado en [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).|  
|[_ATL_WIN_MODULE](#_atl_win_module)|Define como un typedef basado en [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|  
|[ATL_URL_PORT](#atl_url_port)|El tipo utilizado por [CUrl](../../atl/reference/curl-class.md) para especificar un número de puerto.|  
|[CComDispatchDriver](#ccomdispatchdriver)|Esta clase administra los punteros de interfaz COM.|  
|[CComGlobalsThreadModel](#ccomglobalsthreadmodel)|El subproceso apropiado llama a métodos del modelo, independientemente de que se utiliza el modelo de subprocesos.|  
|[CComObjectThreadModel](#ccomobjectthreadmodel)|El subproceso apropiado llama a métodos del modelo, independientemente de que se utiliza el modelo de subprocesos.|  
|[CContainedWindow](#ccontainedwindow)|Esta clase es una especialización de **CContainedWindowT.**|  
|[CPath](#cpath)|Una especialización de [CPathT](../../atl/reference/cpatht-class.md) con `CString`.|  
|[CPathA](#cpatha)|Una especialización de [CPathT](../../atl/reference/cpatht-class.md) con `CStringA`.|  
|[CPathW](#cpathw)|Una especialización de [CPathT](../../atl/reference/cpatht-class.md) con `CStringW`.|  
|[CSimpleValArray](#csimplevalarray)|Representa una matriz para almacenar tipos simples.|  
|[DefaultThreadTraits](#defaultthreadtraits)|La clase de rasgos de subprocesos de forma predeterminada.|  
|[LPCURL](#lpcurl)|Un puntero a una constante [CUrl](../../atl/reference/curl-class.md) objeto.|  
|[LPURL](#lpurl)|Un puntero a un [CUrl](../../atl/reference/curl-class.md) objeto.|  
  
##  <a name="_atl_base_module"></a>_ATL_BASE_MODULE  
 Se define como un typedef basado en _ATL_BASE_MODULE70.  
  
```   
typedef ATL::_ATL_BASE_MODULE70 _ATL_BASE_MODULE;   
```  
  
### <a name="remarks"></a>Comentarios  
 Se utiliza en todos los proyectos ATL. Basado en [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).  
  
 La estructura _ATL_BASE_MODULE se derivan de las clases que forman parte de las clases de módulo ATL 7.0.  Para obtener más información sobre las clases de módulo ATL, consulte [clases de módulos COM](../../atl/com-modules-classes.md).  
  
##  <a name="_atl_com_module"></a>_ATL_COM_MODULE  
 Se define como un typedef basado en _ATL_COM_MODULE70.  
  
```   
typedef ATL::_ATL_COM_MODULE70 _ATL_COM_MODULE;   
```  
  
### <a name="remarks"></a>Comentarios  
 ATL (proyectos) que utilice funciones COM utilizan. Basado en [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).  
  
##  <a name="_atl_module"></a>_ATL_MODULE  
 Se define como un typedef basado en _ATL_MODULE70.  
  
```   
typedef ATL::_ATL_MODULE70 _ATL_MODULE;   
```  
  
### <a name="remarks"></a>Comentarios  
 Basado en [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).  
  
##  <a name="_atl_win_module"></a>_ATL_WIN_MODULE  
 Se define como un typedef basado en _ATL_WIN_MODULE70.  
  
```   
typedef ATL::_ATL_WIN_MODULE70 _ATL_WIN_MODULE; 
 
```  
  
### <a name="remarks"></a>Comentarios  
 Utilizado por los proyectos ATL que usan características de la ventana. Basado en [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md).  
  
##  <a name="atl_url_port"></a>ATL_URL_PORT 
  El tipo utilizado por [CUrl](curl-class.md) para especificar un número de puerto.
```  
typedef WORD ATL_URL_PORT;
```  

##  <a name="ccomdispatchdriver"></a>CComDispatchDriver  
 Esta clase administra los punteros de interfaz COM.  
  
```   
typedef CComQIPtr<IDispatch, &__uuidof(IDispatch)> CComDispatchDriver;   
```  
  
##  <a name="ccomglobalsthreadmodel"></a>CComGlobalsThreadModel  
 El subproceso apropiado llama a métodos del modelo, independientemente de que se utiliza el modelo de subprocesos.  
  
```   
#if defined(_ATL_SINGLE_THREADED)  
typedef CComSingleThreadModel CComGlobalsThreadModel;  
#elif defined(_ATL_APARTMENT_THREADED)  
typedef CComMultiThreadModel CComGlobalsThreadModel;  
#elif defined(_ATL_FREE_THREADED)  
typedef CComMultiThreadModel CComGlobalsThreadModel;  
#else  
#pragma message ("No global threading model defined")  
#endif   
```  
  
### <a name="remarks"></a>Comentarios  
 Según el modelo de subprocesos utilizado por la aplicación, el `typedef` nombre `CComGlobalsThreadModel` hace referencia a cualquiera [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) o [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Estas clases proporcionan adicionales `typedef` nombres hacer referencia a una clase de sección crítica.  
  
> [!NOTE]
> `CComGlobalsThreadModel`no se hace referencia la clase [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).  
  
 Mediante `CComGlobalsThreadModel` evita tener que especificar una determinada clase de modelo de subprocesamiento. Independientemente del modelo de subprocesamiento que se usa, se llamará a los métodos adecuados.  
  
 Además `CComGlobalsThreadModel`, ATL proporciona el `typedef` nombre [CComObjectThreadModel](#ccomobjectthreadmodel). La clase hace referencia a cada `typedef` depende del modelo de subprocesos utilizado, como se muestra en la tabla siguiente:  
  
|definición de tipos|Subprocesamiento único|Subproceso de apartamento|Subprocesamiento libre|  
|-------------|----------------------|-------------------------|--------------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 S= `CComSingleThreadModel`; M =`CComMultiThreadModel`  
  
 Use `CComObjectThreadModel` dentro de una clase de objeto único. Use `CComGlobalsThreadModel` en un objeto que están disponible globalmente para el programa, o cuando desee proteger los recursos de módulo en varios subprocesos.  
  
##  <a name="ccomobjectthreadmodel"></a>CComObjectThreadModel  
 El subproceso apropiado llama a métodos del modelo, independientemente de que se utiliza el modelo de subprocesos.  
  
```   
#if defined(_ATL_SINGLE_THREADED)  
typedef CComSingleThreadModel CComObjectThreadModel;  
#elif defined(_ATL_APARTMENT_THREADED)  
typedef CComSingleThreadModel CComObjectThreadModel;  
#elif defined(_ATL_FREE_THREADED)  
typedef CComMultiThreadModel CComObjectThreadModel;  
#else  
#pragma message ("No global threading model defined")  
#endif   
```  
  
### <a name="remarks"></a>Comentarios  
 Según el modelo de subprocesos utilizado por la aplicación, el `typedef` nombre `CComObjectThreadModel` hace referencia a cualquiera [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) o [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Estas clases proporcionan adicionales `typedef` nombres hacer referencia a una clase de sección crítica.  
  
> [!NOTE]
> `CComObjectThreadModel`no se hace referencia la clase [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).  
  
 Mediante `CComObjectThreadModel` evita tener que especificar una determinada clase de modelo de subprocesamiento. Independientemente del modelo de subprocesamiento que se usa, se llamará a los métodos adecuados.  
  
 Además `CComObjectThreadModel`, ATL proporciona el `typedef` nombre [CComGlobalsThreadModel](#ccomglobalsthreadmodel). La clase hace referencia a cada `typedef` depende del modelo de subprocesos utilizado, como se muestra en la tabla siguiente:  
  
|definición de tipos|Subprocesamiento único|Subproceso de apartamento|Subprocesamiento libre|  
|-------------|----------------------|-------------------------|--------------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 S= `CComSingleThreadModel`; M =`CComMultiThreadModel`  
  
 Use `CComObjectThreadModel` dentro de una clase de objeto único. Use `CComGlobalsThreadModel` en un objeto que está disponible globalmente para el programa o cuando desea proteger los recursos de módulo en varios subprocesos.  
  
##  <a name="ccontainedwindow"></a>CContainedWindow  
 Esta clase es una especialización de **CContainedWindowT.**  
  
```   
typedef CContainedWindowT<CWindow> CContainedWindow;   
```  
  
### <a name="remarks"></a>Comentarios  
 `CContainedWindow`es una especialización de [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md). Si desea cambiar la clase base o rasgos, use `CContainedWindowT` directamente.  
  
##  <a name="cpath"></a>CPath  
 Una especialización de [CPathT](../../atl/reference/cpatht-class.md) con `CString`.  
  
```   
typedef CPathT<CString> CPath;   
```  
  
##  <a name="cpatha"></a>CPathA  
 Una especialización de [CPathT](../../atl/reference/cpatht-class.md) con `CStringA`.  
  
```   
typedef CPathT<CStringA> CPathA;   
```  
  
##  <a name="cpathw"></a>CPathW  
 Una especialización de [CPathT](../../atl/reference/cpatht-class.md) con `CStringW`.  
  
```   
typedef ATL::CPathT<CStringW> CPathW;   
```  
  
##  <a name="csimplevalarray"></a>CSimpleValArray  
 Representa una matriz para almacenar tipos simples.  
  
```   
#define CSimpleValArray CSimpleArray   
```  
  
### <a name="remarks"></a>Comentarios  
 `CSimpleValArray`se proporciona para crear y administrar matrices que contienen tipos de datos simples. Es un simple #define de [CSimpleArray](../../atl/reference/csimplearray-class.md).  
  
##  <a name="lpcurl"></a>LPCURL  
 Un puntero a una constante [CUrl](../../atl/reference/curl-class.md) objeto.  
  
```   
typedef const CUrl* LPCURL;   
```  

##  <a name="defaultthreadtraits"></a>DefaultThreadTraits
La clase de rasgos de subprocesos de forma predeterminada.

### <a name="syntax"></a>Sintaxis
```  
      #if defined(_MT)  
   typedef CRTThreadTraits DefaultThreadTraits;  
#else  
   typedef Win32ThreadTraits DefaultThreadTraits;  
#endif  
```

## <a name="remarks"></a>Comentarios
Si el proyecto actual utiliza CRT multiproceso, DefaultThreadTraits se define como CRTThreadTraits. De lo contrario, se utiliza Win32ThreadTraits.
  
##  <a name="lpurl"></a>LPURL  
 Un puntero a un [CUrl](../../atl/reference/curl-class.md) objeto.  
  
```   
typedef CUrl* LPURL;   
```  
  
## <a name="see-also"></a>Vea también  
 [Componentes de escritorio de COM de ATL](../../atl/atl-com-desktop-components.md)   
 [Funciones](../../atl/reference/atl-functions.md)   
 [Variables globales](../../atl/reference/atl-global-variables.md)   
 [Estructuras](../../atl/reference/atl-structures.md)   
 [Macros](../../atl/reference/atl-macros.md)   
 [Clases](../../atl/reference/atl-classes.md)
