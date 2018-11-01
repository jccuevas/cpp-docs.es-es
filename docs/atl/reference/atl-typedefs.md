---
title: Typedefs ATL
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
ms.openlocfilehash: c723d76f17ad1c74ab98e7348450cea3f03c4d78
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429320"
---
# <a name="atl-typedefs"></a>Typedefs ATL

Active Template Library incluye las siguientes definiciones de tipo.

|||
|-|-|
|[_ATL_BASE_MODULE](#_atl_base_module)|Definido como una definición de tipo según [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).|
|[_ATL_COM_MODULE](#_atl_com_module)|Definido como una definición de tipo según [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).|
|[_ATL_MODULE](#_atl_module)|Definido como una definición de tipo según [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).|
|[_ATL_WIN_MODULE](#_atl_win_module)|Definido como una definición de tipo según [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|
|[ATL_URL_PORT](#atl_url_port)|El tipo utilizado por [CUrl](../../atl/reference/curl-class.md) para especificar un número de puerto.|
|[CComDispatchDriver](#ccomdispatchdriver)|Esta clase administra los punteros de interfaz COM.|
|[CComGlobalsThreadModel](#ccomglobalsthreadmodel)|Llama a métodos del modelo, independientemente del modelo de subprocesamiento que se va a usar el subproceso adecuado.|
|[CComObjectThreadModel](#ccomobjectthreadmodel)|Llama a métodos del modelo, independientemente del modelo de subprocesamiento que se va a usar el subproceso adecuado.|
|[CContainedWindow](#ccontainedwindow)|Esta clase es una especialización de `CContainedWindowT`.|
|[CPath](#cpath)|Una especialización de [CPathT](../../atl/reference/cpatht-class.md) mediante `CString`.|
|[CPathA](#cpatha)|Una especialización de [CPathT](../../atl/reference/cpatht-class.md) mediante `CStringA`.|
|[CPathW](#cpathw)|Una especialización de [CPathT](../../atl/reference/cpatht-class.md) mediante `CStringW`.|
|[CSimpleValArray](#csimplevalarray)|Representa una matriz para almacenar tipos simples.|
|[DefaultThreadTraits](#defaultthreadtraits)|La clase de rasgos de subproceso de forma predeterminada.|
|[LPCURL](#lpcurl)|Un puntero a una constante [CUrl](../../atl/reference/curl-class.md) objeto.|
|[LPURL](#lpurl)|Un puntero a un [CUrl](../../atl/reference/curl-class.md) objeto.|

##  <a name="_atl_base_module"></a>  _ATL_BASE_MODULE

Se define como una definición de tipo según _ATL_BASE_MODULE70.

```
typedef ATL::_ATL_BASE_MODULE70 _ATL_BASE_MODULE;
```

### <a name="remarks"></a>Comentarios

Se utiliza en todos los proyectos ATL. En función de [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).

La estructura _ATL_BASE_MODULE se derivan de las clases que forman parte de las clases de módulo ATL 7.0.  Para obtener más información sobre las clases de módulo de ATL, consulte [clases de módulos de COM](../../atl/com-modules-classes.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcore.h

##  <a name="_atl_com_module"></a>  _ATL_COM_MODULE

Se define como una definición de tipo según _ATL_COM_MODULE70.

```
typedef ATL::_ATL_COM_MODULE70 _ATL_COM_MODULE;
```

### <a name="remarks"></a>Comentarios

Usar los proyectos ATL que usan características COM. En función de [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

##  <a name="_atl_module"></a>  _ATL_MODULE

Se define como una definición de tipo según _ATL_MODULE70.

```
typedef ATL::_ATL_MODULE70 _ATL_MODULE;
```

## <a name="requirements"></a>Requisitos

**Encabezado:**

### <a name="remarks"></a>Comentarios

En función de [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).

##  <a name="_atl_win_module"></a>  _ATL_WIN_MODULE

Se define como una definición de tipo según _ATL_WIN_MODULE70.

```
typedef ATL::_ATL_WIN_MODULE70 _ATL_WIN_MODULE;
```

### <a name="remarks"></a>Comentarios

Usa los proyectos ATL que usan características de la ventana. En función de [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

##  <a name="atl_url_port"></a>  ATL_URL_PORT

El tipo utilizado por [CUrl](curl-class.md) para especificar un número de puerto.

```
typedef WORD ATL_URL_PORT;
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atlutil.h

##  <a name="ccomdispatchdriver"></a>  CComDispatchDriver

Esta clase administra los punteros de interfaz COM.

```
typedef CComQIPtr<IDispatch, &__uuidof(IDispatch)> CComDispatchDriver;
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

##  <a name="ccomglobalsthreadmodel"></a>  CComGlobalsThreadModel

Llama a métodos del modelo, independientemente del modelo de subprocesamiento que se va a usar el subproceso adecuado.

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

Según el modelo de subprocesos utilizado por la aplicación, el **typedef** nombre `CComGlobalsThreadModel` hace referencia a [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) o [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Estas clases proporcionan adicionales `typedef` nombres hacer referencia a una clase de sección crítica.

> [!NOTE]
> `CComGlobalsThreadModel` no hace referencia a clase [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).

Uso de `CComGlobalsThreadModel` evita que se especifica una clase de modelo de subprocesos determinado. Independientemente del modelo de subprocesamiento que se va a usar, se llamará a los métodos adecuados.

Además `CComGlobalsThreadModel`, ATL proporciona el **typedef** nombre [CComObjectThreadModel](#ccomobjectthreadmodel). La clase que se hace referencia a cada uno de ellos `typedef` depende del modelo de subprocesos utilizado, tal como se muestra en la tabla siguiente:

|typedef|Subprocesamiento único|Apartamento de subproceso|Subprocesamiento libre|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`; M = `CComMultiThreadModel`

Use `CComObjectThreadModel` dentro de una clase de objeto único. Use `CComGlobalsThreadModel` en un objeto que está disponible globalmente para el programa, o si desea proteger los recursos de módulo en varios subprocesos.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

##  <a name="ccomobjectthreadmodel"></a>  CComObjectThreadModel

Llama a métodos del modelo, independientemente del modelo de subprocesamiento que se va a usar el subproceso adecuado.

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

Según el modelo de subprocesos utilizado por la aplicación, el `typedef` nombre `CComObjectThreadModel` hace referencia a [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) o [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Estas clases proporcionan adicionales `typedef` nombres hacer referencia a una clase de sección crítica.

> [!NOTE]
> `CComObjectThreadModel` no hace referencia a clase [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).

Uso de `CComObjectThreadModel` evita que se especifica una clase de modelo de subprocesos determinado. Independientemente del modelo de subprocesamiento que se va a usar, se llamará a los métodos adecuados.

Además `CComObjectThreadModel`, ATL proporciona el **typedef** nombre [CComGlobalsThreadModel](#ccomglobalsthreadmodel). La clase que se hace referencia a cada uno de ellos **typedef** depende del modelo de subprocesos utilizado, tal como se muestra en la tabla siguiente:

|typedef|Subprocesamiento único|Apartamento de subproceso|Subprocesamiento libre|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`; M = `CComMultiThreadModel`

Use `CComObjectThreadModel` dentro de una clase de objeto único. Use `CComGlobalsThreadModel` en un objeto que sea globalmente disponible para el programa, o cuando desea proteger los recursos de módulo en varios subprocesos.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

##  <a name="ccontainedwindow"></a>  CContainedWindow

Esta clase es una especialización de `CContainedWindowT`.

```
typedef CContainedWindowT<CWindow> CContainedWindow;
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

### <a name="remarks"></a>Comentarios

`CContainedWindow` es una especialización de [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md). Si desea cambiar la clase base o rasgos, utilice `CContainedWindowT` directamente.

##  <a name="cpath"></a>  CPath

Una especialización de [CPathT](../../atl/reference/cpatht-class.md) mediante `CString`.

```
typedef CPathT<CString> CPath;
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atlpath.h

##  <a name="cpatha"></a>  CPathA

Una especialización de [CPathT](../../atl/reference/cpatht-class.md) mediante `CStringA`.

```
typedef CPathT<CStringA> CPathA;
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atlpath.h

##  <a name="cpathw"></a>  CPathW

Una especialización de [CPathT](../../atl/reference/cpatht-class.md) mediante `CStringW`.

```
typedef ATL::CPathT<CStringW> CPathW;
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atlpath.h

##  <a name="csimplevalarray"></a>  CSimpleValArray

Representa una matriz para almacenar tipos simples.

```
#define CSimpleValArray CSimpleArray
```

### <a name="remarks"></a>Comentarios

`CSimpleValArray` se proporciona para crear y administrar matrices que contienen tipos de datos simples. Es una sencilla #define de [CSimpleArray](../../atl/reference/csimplearray-class.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsimpcoll.h

##  <a name="lpcurl"></a>  LPCURL

Un puntero a una constante [CUrl](../../atl/reference/curl-class.md) objeto.

```
typedef const CUrl* LPCURL;
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atlutil.h

##  <a name="defaultthreadtraits"></a>  DefaultThreadTraits

La clase de rasgos de subproceso de forma predeterminada.

### <a name="syntax"></a>Sintaxis

```
#if defined(_MT)
   typedef CRTThreadTraits DefaultThreadTraits;
#else
   typedef Win32ThreadTraits DefaultThreadTraits;
#endif
```

## <a name="remarks"></a>Comentarios

Si el proyecto actual usa CRT multiproceso, DefaultThreadTraits se define como CRTThreadTraits. En caso contrario, se usa Win32ThreadTraits.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

##  <a name="lpurl"></a>  LPURL

Un puntero a un [CUrl](../../atl/reference/curl-class.md) objeto.

```
typedef CUrl* LPURL;
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atlutil.h

## <a name="see-also"></a>Vea también

[Componentes de escritorio COM de ATL](../../atl/atl-com-desktop-components.md)<br/>
[Funciones](../../atl/reference/atl-functions.md)<br/>
[Variables globales](../../atl/reference/atl-global-variables.md)<br/>
[Clases y structs](../../atl/reference/atl-classes.md)<br/>
[Macros](../../atl/reference/atl-macros.md)
