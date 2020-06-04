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
ms.openlocfilehash: 26e4e80ed3110351130731e6030427d25fc4a0ea
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168740"
---
# <a name="atl-typedefs"></a>Definiciones de tipo ATL

El Active Template Library incluye las siguientes definiciones de código.

|||
|-|-|
|[_ATL_BASE_MODULE](#_atl_base_module)|Se define como una definición de tipo basada en [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).|
|[_ATL_COM_MODULE](#_atl_com_module)|Se define como una definición de tipo basada en [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).|
|[_ATL_MODULE](#_atl_module)|Se define como una definición de tipo basada en [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).|
|[_ATL_WIN_MODULE](#_atl_win_module)|Definido como una definición de tipo basada en [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|
|[ATL_URL_PORT](#atl_url_port)|Tipo utilizado por [rizo](../../atl/reference/curl-class.md) para especificar un número de puerto.|
|[CComDispatchDriver](#ccomdispatchdriver)|Esta clase administra punteros de interfaz COM.|
|[CComGlobalsThreadModel](#ccomglobalsthreadmodel)|Llama a los métodos de modelo de subproceso adecuados, independientemente del modelo de subprocesos que se utilice.|
|[CComObjectThreadModel](#ccomobjectthreadmodel)|Llama a los métodos de modelo de subproceso adecuados, independientemente del modelo de subprocesos que se utilice.|
|[CContainedWindow](#ccontainedwindow)|Esta clase es una especialización de `CContainedWindowT`.|
|[CPath](#cpath)|Una especialización de [CPathT](../../atl/reference/cpatht-class.md) mediante `CString`.|
|[CPathA](#cpatha)|Una especialización de [CPathT](../../atl/reference/cpatht-class.md) mediante `CStringA`.|
|[CPathW](#cpathw)|Una especialización de [CPathT](../../atl/reference/cpatht-class.md) mediante `CStringW`.|
|[CSimpleValArray](#csimplevalarray)|Representa una matriz para almacenar tipos simples.|
|[DefaultThreadTraits](#defaultthreadtraits)|La clase de rasgos de subprocesos predeterminada.|
|[LPCURL](#lpcurl)|Un puntero a un objeto de [rizo](../../atl/reference/curl-class.md) de constante.|
|[LPURL](#lpurl)|Un puntero a un objeto de [rizo](../../atl/reference/curl-class.md) .|

## <a name="_atl_base_module"></a><a name="_atl_base_module"></a>_ATL_BASE_MODULE

Se define como una definición de tipo basada en _ATL_BASE_MODULE70.

```cpp
typedef ATL::_ATL_BASE_MODULE70 _ATL_BASE_MODULE;
```

### <a name="remarks"></a>Observaciones

Se usa en cada proyecto ATL. Basado en [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).

Las clases que forman parte de las clases de módulo ATL 7,0 derivan de la estructura _ATL_BASE_MODULE.  Para obtener más información sobre las clases de módulo ATL, consulte [clases de módulos com](../../atl/com-modules-classes.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** atlcore. h

## <a name="_atl_com_module"></a><a name="_atl_com_module"></a>_ATL_COM_MODULE

Se define como una definición de tipo basada en _ATL_COM_MODULE70.

```cpp
typedef ATL::_ATL_COM_MODULE70 _ATL_COM_MODULE;
```

### <a name="remarks"></a>Observaciones

Lo usan los proyectos ATL que utilizan características COM. Basado en [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

## <a name="_atl_module"></a><a name="_atl_module"></a>_ATL_MODULE

Se define como una definición de tipo basada en _ATL_MODULE70.

```cpp
typedef ATL::_ATL_MODULE70 _ATL_MODULE;
```

### <a name="requirements"></a>Requisitos

**Encabezado**

### <a name="remarks"></a>Observaciones

Basado en [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).

## <a name="_atl_win_module"></a><a name="_atl_win_module"></a>_ATL_WIN_MODULE

Se define como una definición de tipo basada en _ATL_WIN_MODULE70.

```cpp
typedef ATL::_ATL_WIN_MODULE70 _ATL_WIN_MODULE;
```

### <a name="remarks"></a>Observaciones

Lo usan los proyectos ATL que utilizan características de ventanas. Basado en [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

## <a name="atl_url_port"></a><a name="atl_url_port"></a>ATL_URL_PORT

Tipo utilizado por [rizo](curl-class.md) para especificar un número de puerto.

```cpp
typedef WORD ATL_URL_PORT;
```

### <a name="requirements"></a>Requisitos

**Encabezado:** atlutil. h

## <a name="ccomdispatchdriver"></a><a name="ccomdispatchdriver"></a>CComDispatchDriver

Esta clase administra punteros de interfaz COM.

```cpp
typedef CComQIPtr<IDispatch, &__uuidof(IDispatch)> CComDispatchDriver;
```

### <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

## <a name="ccomglobalsthreadmodel"></a><a name="ccomglobalsthreadmodel"></a>CComGlobalsThreadModel

Llama a los métodos de modelo de subproceso adecuados, independientemente del modelo de subprocesos que se utilice.

```cpp
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

Dependiendo del modelo de subprocesos utilizado por la aplicación, el **typedef** nombre `CComGlobalsThreadModel` typedef hace referencia a [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) o [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Estas clases proporcionan nombres `typedef` adicionales para hacer referencia a una clase de sección crítica.

> [!NOTE]
> `CComGlobalsThreadModel`no hace referencia a la clase [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).

Usar `CComGlobalsThreadModel` le libera de especificar una clase de modelo de subprocesos determinada. Independientemente del modelo de subprocesos que se use, se llamará a los métodos apropiados.

Además de `CComGlobalsThreadModel`, ATL proporciona el nombre de **definición** de tipo [CComObjectThreadModel](#ccomobjectthreadmodel). La clase a la que hace `typedef` referencia depende del modelo de subprocesos utilizado, tal como se muestra en la tabla siguiente:

|typedef|Subprocesamiento único|Subprocesamiento de apartamento|Subprocesamiento libre|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`; M =`CComMultiThreadModel`

Se `CComObjectThreadModel` usa dentro de una clase de objeto única. Use `CComGlobalsThreadModel` en un objeto que esté disponible globalmente para el programa, o cuando desee proteger los recursos de módulo en varios subprocesos.

### <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

## <a name="ccomobjectthreadmodel"></a><a name="ccomobjectthreadmodel"></a>CComObjectThreadModel

Llama a los métodos de modelo de subproceso adecuados, independientemente del modelo de subprocesos que se utilice.

```cpp
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

Dependiendo del modelo de subprocesos utilizado por la aplicación, el `typedef` nombre `CComObjectThreadModel` hace referencia a [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) o [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Estas clases proporcionan nombres `typedef` adicionales para hacer referencia a una clase de sección crítica.

> [!NOTE]
> `CComObjectThreadModel`no hace referencia a la clase [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).

Usar `CComObjectThreadModel` le libera de especificar una clase de modelo de subprocesos determinada. Independientemente del modelo de subprocesos que se use, se llamará a los métodos apropiados.

Además de `CComObjectThreadModel`, ATL proporciona el nombre de **definición** de tipo [CComGlobalsThreadModel](#ccomglobalsthreadmodel). La clase a la que hace referencia cada **typedef** depende del modelo de subprocesos utilizado, tal como se muestra en la tabla siguiente:

|typedef|Subprocesamiento único|Subprocesamiento de apartamento|Subprocesamiento libre|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`; M =`CComMultiThreadModel`

Se `CComObjectThreadModel` usa dentro de una clase de objeto única. Use `CComGlobalsThreadModel` en un objeto que esté disponible globalmente para el programa o si desea proteger los recursos del módulo en varios subprocesos.

### <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

## <a name="ccontainedwindow"></a><a name="ccontainedwindow"></a>CContainedWindow

Esta clase es una especialización de `CContainedWindowT`.

```cpp
typedef CContainedWindowT<CWindow> CContainedWindow;
```

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin. h

### <a name="remarks"></a>Observaciones

`CContainedWindow`es una especialización de [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md). Si desea cambiar la clase base o rasgos, use `CContainedWindowT` directamente.

## <a name="cpath"></a><a name="cpath"></a>CPath

Una especialización de [CPathT](../../atl/reference/cpatht-class.md) mediante `CString`.

```cpp
typedef CPathT<CString> CPath;
```

### <a name="requirements"></a>Requisitos

**Encabezado:** atlpath. h

## <a name="cpatha"></a><a name="cpatha"></a>CPathA

Una especialización de [CPathT](../../atl/reference/cpatht-class.md) mediante `CStringA`.

```cpp
typedef CPathT<CStringA> CPathA;
```

### <a name="requirements"></a>Requisitos

**Encabezado:** atlpath. h

## <a name="cpathw"></a><a name="cpathw"></a>CPathW

Una especialización de [CPathT](../../atl/reference/cpatht-class.md) mediante `CStringW`.

```cpp
typedef ATL::CPathT<CStringW> CPathW;
```

### <a name="requirements"></a>Requisitos

**Encabezado:** atlpath. h

## <a name="csimplevalarray"></a><a name="csimplevalarray"></a>CSimpleValArray

Representa una matriz para almacenar tipos simples.

```cpp
#define CSimpleValArray CSimpleArray
```

### <a name="remarks"></a>Observaciones

`CSimpleValArray`se proporciona para crear y administrar matrices que contienen tipos de datos simples. Es una #define sencilla de [CSimpleArray](../../atl/reference/csimplearray-class.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** atlsimpcoll. h

## <a name="lpcurl"></a><a name="lpcurl"></a>LPCURL

Un puntero a un objeto de [rizo](../../atl/reference/curl-class.md) de constante.

```cpp
typedef const CUrl* LPCURL;
```

### <a name="requirements"></a>Requisitos

**Encabezado:** atlutil. h

## <a name="defaultthreadtraits"></a><a name="defaultthreadtraits"></a>DefaultThreadTraits

La clase de rasgos de subprocesos predeterminada.

### <a name="syntax"></a>Sintaxis

```cpp
#if defined(_MT)
   typedef CRTThreadTraits DefaultThreadTraits;
#else
   typedef Win32ThreadTraits DefaultThreadTraits;
#endif
```

## <a name="remarks"></a>Observaciones

Si el proyecto actual usa CRT multiproceso, DefaultThreadTraits se define como CRTThreadTraits. De lo contrario, se utiliza Win32ThreadTraits.

### <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

## <a name="lpurl"></a><a name="lpurl"></a>LPURL

Un puntero a un objeto de [rizo](../../atl/reference/curl-class.md) .

```cpp
typedef CUrl* LPURL;
```

### <a name="requirements"></a>Requisitos

**Encabezado:** atlutil. h

## <a name="see-also"></a>Consulte también

[Componentes de escritorio COM de ATL](../../atl/atl-com-desktop-components.md)<br/>
[Functions](../../atl/reference/atl-functions.md)<br/>
[Variables globales](../../atl/reference/atl-global-variables.md)<br/>
[Clases y estructuras](../../atl/reference/atl-classes.md)<br/>
[Macros](../../atl/reference/atl-macros.md)
