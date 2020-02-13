---
title: CComPtr (clase)
description: Guía de referencia de la C++ Clase CComPtr de Microsoft Active Template Library (ATL).
ms.date: 02/07/2020
f1_keywords:
- CComPtr
- ATLBASE/ATL::CComPtr
- ATLBASE/ATL::CComPtr::CComPtr
helpviewer_keywords:
- CComPtr class
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
ms.openlocfilehash: 74a12b460f55a782fa2747b02f7d00287786fae6
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127412"
---
# <a name="ccomptr-class"></a>CComPtr (clase)

Una clase de puntero inteligente para administrar punteros de interfaz COM.

## <a name="syntax"></a>Sintaxis

```cpp
template<class T>
class CComPtr
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Una interfaz COM que especifica el tipo de puntero que se va a almacenar.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComPtr:: CComPtr](#ccomptr)|El constructor.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComPtr:: Operator =](#operator_eq)|Asigna un puntero al puntero de miembro.|

## <a name="remarks"></a>Observaciones

ATL usa `CComPtr` y [CComQIPtr](../../atl/reference/ccomqiptr-class.md) para administrar punteros de interfaz com. Ambos se derivan de [CComPtrBase](../../atl/reference/ccomptrbase-class.md)y ambos realizan el recuento de referencias automático.

Las clases `CComPtr` y [CComQIPtr](../../atl/reference/ccomqiptr-class.md) pueden ayudar a eliminar pérdidas de memoria al realizar el recuento de referencias automático.  Las siguientes funciones realizan las mismas operaciones lógicas. Sin embargo, la segunda versión puede ser menos propensa a errores porque utiliza la clase `CComPtr`:

[!code-cpp[NVC_ATL_Utilities#130](../../atl/codesnippet/cpp/ccomptr-class_1.cpp)]

[!code-cpp[NVC_ATL_Utilities#131](../../atl/codesnippet/cpp/ccomptr-class_2.cpp)]

En compilaciones de depuración, vincule atlsd. lib para el seguimiento del código.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

`CComPtr`

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

## <a name="ccomptr"></a>CComPtr:: CComPtr

El constructor.

```cpp
CComPtr() throw ();
CComPtr(T* lp) throw ();
CComPtr (const CComPtr<T>& lp) throw ();
```

### <a name="parameters"></a>Parámetros

*LP*<br/>
Se usa para inicializar el puntero de interfaz.

*T*<br/>
Una interfaz COM.

### <a name="remarks"></a>Observaciones

Los constructores que toman una llamada de argumento `AddRef` en *LP*, si no es un puntero nulo. Un objeto propiedad no NULL obtiene una llamada `Release` en la destrucción del objeto CComPtr o si se asigna un nuevo objeto al objeto CComPtr.

## <a name="operator_eq"></a>CComPtr:: Operator =

Operador de asignación.

```cpp
T* operator= (T* lp) throw ();
T* operator= (const CComPtr<T>& lp) throw ();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al objeto `CComPtr` actualizado

### <a name="remarks"></a>Observaciones

Esta operación AddRefs el nuevo objeto y libera el objeto existente, si existe.

## <a name="see-also"></a>Consulte también

[CComPtr:: CComPtr](#ccomptr)<br/>
[CComQIPtr:: CComQIPtr](../../atl/reference/ccomqiptr-class.md#ccomqiptr)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
