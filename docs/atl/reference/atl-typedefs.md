---
title: Definiciones de tipo ATL
ms.date: 11/04/2016
f1_keywords:
- atlcore/ATL::_ATL_BASE_MODULE
- atlbase/ATL::_ATL_COM_MODULE
- atlbase/ATL::_ATL_MODULE
- atlbase/ATL::_ATL_WIN_MODULE
- atlutil/ATL::ATL_URL_PORT
- atlbase/ATL::CComDispatchDriver
- atlbase/ATL::CComGlobalsThreadModel
- atlbase/ATL::CComObjectThreadModel
- atlwin/ATL::CContainedWindow
- atlpath/ATL::CPath
- atlpath/ATL::CPathA
- atlpath/ATL::CPathW
- " atlsimpcoll/ATL::CSimpleValArray"
- " atlutil/ATL::LPCURL"
- atlbase/ATL::DefaultThreadTraits
- atlutil/ATL::LPURL
helpviewer_keywords:
- typedefs, ATL
- typedefs
- ATL, typedefs
ms.assetid: 7dd05baa-3efb-4e3b-af23-793c610f4560
ms.openlocfilehash: 5548bee36ac52dbd6add31241714b0404289be45
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319196"
---
# <a name="atl-typedefs"></a>Definiciones de tipo ATL

La biblioteca de plantillas activas incluye las siguientes desfs de tipo.

|||
|-|-|
|[_ATL_BASE_MODULE](#_atl_base_module)|Definido como typedef basado en [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).|
|[_ATL_COM_MODULE](#_atl_com_module)|Definido como typedef basado en [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).|
|[_ATL_MODULE](#_atl_module)|Definido como typedef basado en [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).|
|[_ATL_WIN_MODULE](#_atl_win_module)|Definido como una definición de tipo basada en [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|
|[ATL_URL_PORT](#atl_url_port)|El tipo utilizado por [CUrl](../../atl/reference/curl-class.md) para especificar un número de puerto.|
|[CComDispatchDriver](#ccomdispatchdriver)|Esta clase administra punteros de interfaz COM.|
|[CComGlobalsThreadModel](#ccomglobalsthreadmodel)|Llama a los métodos de modelo de subprocesos adecuados, independientemente del modelo de subprocesos que se use.|
|[CComObjectThreadModel](#ccomobjectthreadmodel)|Llama a los métodos de modelo de subprocesos adecuados, independientemente del modelo de subprocesos que se use.|
|[CContainedWindow](#ccontainedwindow)|Esta clase es `CContainedWindowT`una especialización de .|
|[CPath](#cpath)|Una especialización de `CString` [CPathT](../../atl/reference/cpatht-class.md) mediante .|
|[CPathA](#cpatha)|Una especialización de `CStringA` [CPathT](../../atl/reference/cpatht-class.md) mediante .|
|[CPathW](#cpathw)|Una especialización de `CStringW` [CPathT](../../atl/reference/cpatht-class.md) mediante .|
|[CSimpleValArray](#csimplevalarray)|Representa una matriz para almacenar tipos simples.|
|[DefaultThreadTraits](#defaultthreadtraits)|La clase de rasgos de subproceso predeterminada.|
|[LPCURL](#lpcurl)|Un puntero a una constante [CUrl](../../atl/reference/curl-class.md) objeto.|
|[LPURL](#lpurl)|Un puntero a un [CUrl](../../atl/reference/curl-class.md) objeto.|

## <a name="_atl_base_module"></a><a name="_atl_base_module"></a>_ATL_BASE_MODULE

Definido como una definición de tipo basada en _ATL_BASE_MODULE70.

```
typedef ATL::_ATL_BASE_MODULE70 _ATL_BASE_MODULE;
```

### <a name="remarks"></a>Observaciones

Se utiliza en todos los proyectos ATL. Basado en [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).

Las clases que forman parte de las clases de módulo ATL 7.0 derivan de la estructura _ATL_BASE_MODULE.  Para más información sobre las clases del módulo ATL, refiera a las clases de [los módulos COM.](../../atl/com-modules-classes.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcore.h

## <a name="_atl_com_module"></a><a name="_atl_com_module"></a>_ATL_COM_MODULE

Definido como una definición de tipo basada en _ATL_COM_MODULE70.

```
typedef ATL::_ATL_COM_MODULE70 _ATL_COM_MODULE;
```

### <a name="remarks"></a>Observaciones

Utilizado por proyectos ATL que utilizan características COM. Basado en [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="_atl_module"></a><a name="_atl_module"></a>_ATL_MODULE

Definido como una definición de tipo basada en _ATL_MODULE70.

```
typedef ATL::_ATL_MODULE70 _ATL_MODULE;
```

## <a name="requirements"></a>Requisitos

**Rúbrica:**

### <a name="remarks"></a>Observaciones

Basado en [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).

## <a name="_atl_win_module"></a><a name="_atl_win_module"></a>_ATL_WIN_MODULE

Definido como una definición de tipo basada en _ATL_WIN_MODULE70.

```
typedef ATL::_ATL_WIN_MODULE70 _ATL_WIN_MODULE;
```

### <a name="remarks"></a>Observaciones

Utilizado por cualquier proyecto ATL que utilice características de ventanas. Basado en [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="atl_url_port"></a><a name="atl_url_port"></a>ATL_URL_PORT

El tipo utilizado por [CUrl](curl-class.md) para especificar un número de puerto.

```
typedef WORD ATL_URL_PORT;
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atlutil.h

## <a name="ccomdispatchdriver"></a><a name="ccomdispatchdriver"></a>CComDispatchDriver

Esta clase administra punteros de interfaz COM.

```
typedef CComQIPtr<IDispatch, &__uuidof(IDispatch)> CComDispatchDriver;
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="ccomglobalsthreadmodel"></a><a name="ccomglobalsthreadmodel"></a>CComGlobalsThreadModel

Llama a los métodos de modelo de subprocesos adecuados, independientemente del modelo de subprocesos que se use.

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

### <a name="remarks"></a>Observaciones

Según el modelo de subprocesos utilizado por la `CComGlobalsThreadModel` aplicación, el nombre **typedef** hace referencia a [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) o [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Estas clases `typedef` proporcionan nombres adicionales para hacer referencia a una clase de sección crítica.

> [!NOTE]
> `CComGlobalsThreadModel`no hace referencia a la clase [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).

El `CComGlobalsThreadModel` uso le libera de especificar una clase de modelo de subprocesos determinada. Independientemente del modelo de subprocesos que se utilice, se llamará a los métodos adecuados.

Además `CComGlobalsThreadModel`de , ATL proporciona el nombre **typedef** [CComObjectThreadModel](#ccomobjectthreadmodel). La clase a `typedef` la que hace referencia cada uno depende del modelo de subprocesos utilizado, como se muestra en la tabla siguiente:

|typedef|Roscado único|Roscado de apartamentos|Roscado libre|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S `CComSingleThreadModel`- ; M-`CComMultiThreadModel`

Utilícelo `CComObjectThreadModel` dentro de una sola clase de objeto. Utilícelo `CComGlobalsThreadModel` en un objeto que esté disponible globalmente para el programa o cuando desee proteger los recursos del módulo en varios subprocesos.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="ccomobjectthreadmodel"></a><a name="ccomobjectthreadmodel"></a>CComObjectThreadModel

Llama a los métodos de modelo de subprocesos adecuados, independientemente del modelo de subprocesos que se use.

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

### <a name="remarks"></a>Observaciones

Según el modelo de subprocesos utilizado `typedef` `CComObjectThreadModel` por la aplicación, el nombre hace referencia a [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) o [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Estas clases `typedef` proporcionan nombres adicionales para hacer referencia a una clase de sección crítica.

> [!NOTE]
> `CComObjectThreadModel`no hace referencia a la clase [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).

El `CComObjectThreadModel` uso le libera de especificar una clase de modelo de subprocesos determinada. Independientemente del modelo de subprocesos que se utilice, se llamará a los métodos adecuados.

Además `CComObjectThreadModel`de , ATL proporciona el nombre **typedef** [CComGlobalsThreadModel](#ccomglobalsthreadmodel). La clase a la que hace referencia cada **typedef** depende del modelo de subprocesos utilizado, como se muestra en la tabla siguiente:

|typedef|Roscado único|Roscado de apartamentos|Roscado libre|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S `CComSingleThreadModel`- ; M-`CComMultiThreadModel`

Utilícelo `CComObjectThreadModel` dentro de una sola clase de objeto. Utilícelo `CComGlobalsThreadModel` en un objeto que esté disponible globalmente para el programa o cuando desee proteger los recursos del módulo en varios subprocesos.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="ccontainedwindow"></a><a name="ccontainedwindow"></a>CContainedWindow

Esta clase es `CContainedWindowT`una especialización de .

```
typedef CContainedWindowT<CWindow> CContainedWindow;
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

### <a name="remarks"></a>Observaciones

`CContainedWindow`es una especialización de [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md). Si desea cambiar la clase base `CContainedWindowT` o los rasgos, utilice directamente.

## <a name="cpath"></a><a name="cpath"></a>CPath

Una especialización de `CString` [CPathT](../../atl/reference/cpatht-class.md) mediante .

```
typedef CPathT<CString> CPath;
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atlpath.h

## <a name="cpatha"></a><a name="cpatha"></a>CPathA

Una especialización de `CStringA` [CPathT](../../atl/reference/cpatht-class.md) mediante .

```
typedef CPathT<CStringA> CPathA;
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atlpath.h

## <a name="cpathw"></a><a name="cpathw"></a>CPathW

Una especialización de `CStringW` [CPathT](../../atl/reference/cpatht-class.md) mediante .

```
typedef ATL::CPathT<CStringW> CPathW;
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atlpath.h

## <a name="csimplevalarray"></a><a name="csimplevalarray"></a>CSimpleValArray

Representa una matriz para almacenar tipos simples.

```
#define CSimpleValArray CSimpleArray
```

### <a name="remarks"></a>Observaciones

`CSimpleValArray`se proporciona para crear y administrar matrices que contienen tipos de datos simples. Es un simple #define de [CSimpleArray](../../atl/reference/csimplearray-class.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsimpcoll.h

## <a name="lpcurl"></a><a name="lpcurl"></a>LPCURL

Un puntero a una constante [CUrl](../../atl/reference/curl-class.md) objeto.

```
typedef const CUrl* LPCURL;
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atlutil.h

## <a name="defaultthreadtraits"></a><a name="defaultthreadtraits"></a>DefaultThreadTraits

La clase de rasgos de subproceso predeterminada.

### <a name="syntax"></a>Sintaxis

```
#if defined(_MT)
   typedef CRTThreadTraits DefaultThreadTraits;
#else
   typedef Win32ThreadTraits DefaultThreadTraits;
#endif
```

## <a name="remarks"></a>Observaciones

Si el proyecto actual utiliza el CRT multiproceso, DefaultThreadTraits se define como CRTThreadTraits. De lo contrario, se utiliza Win32ThreadTraits.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="lpurl"></a><a name="lpurl"></a>LPURL

Un puntero a un [CUrl](../../atl/reference/curl-class.md) objeto.

```
typedef CUrl* LPURL;
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atlutil.h

## <a name="see-also"></a>Consulte también

[Componentes de escritorio COM de ATL](../../atl/atl-com-desktop-components.md)<br/>
[Functions](../../atl/reference/atl-functions.md)<br/>
[Variables globales](../../atl/reference/atl-global-variables.md)<br/>
[Clases y estructuras](../../atl/reference/atl-classes.md)<br/>
[Macros](../../atl/reference/atl-macros.md)
