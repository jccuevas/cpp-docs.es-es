---
title: Clase CComPtr
description: Guía de referencia para la clase CComPtr de la biblioteca de plantillas activas (ATL) de Microsoft C++ .
ms.date: 02/07/2020
f1_keywords:
- CComPtr
- ATLBASE/ATL::CComPtr
- ATLBASE/ATL::CComPtr::CComPtr
helpviewer_keywords:
- CComPtr class
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
ms.openlocfilehash: 855466225db2672755658dcbbc9a266d09e0e7be
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327524"
---
# <a name="ccomptr-class"></a>Clase CComPtr

Una clase de puntero inteligente para administrar punteros de interfaz COM.

## <a name="syntax"></a>Sintaxis

```cpp
template<class T>
class CComPtr
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Interfaz COM que especifica el tipo de puntero que se va a almacenar.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComPtr::CComPtr](#ccomptr)|El constructor.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComPtr::operador ?](#operator_eq)|Asigna un puntero al puntero de miembro.|

## <a name="remarks"></a>Observaciones

ATL `CComPtr` utiliza y [CComQIPtr](../../atl/reference/ccomqiptr-class.md) para administrar punteros de interfaz COM. Ambos se derivan de [CComPtrBase](../../atl/reference/ccomptrbase-class.md), y ambos hacen recuento automático de referencias.

Las `CComPtr` clases y [CComQIPtr](../../atl/reference/ccomqiptr-class.md) pueden ayudar a eliminar las pérdidas de memoria mediante la realización de recuento automático de referencias.  Las siguientes funciones realizan las mismas operaciones lógicas. Sin embargo, la segunda versión puede `CComPtr` ser menos propensa a errores porque utiliza la clase:

[!code-cpp[NVC_ATL_Utilities#130](../../atl/codesnippet/cpp/ccomptr-class_1.cpp)]

[!code-cpp[NVC_ATL_Utilities#131](../../atl/codesnippet/cpp/ccomptr-class_2.cpp)]

En compilaciones de depuración, vincule atlsd.lib para el seguimiento de código.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

`CComPtr`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="ccomptrccomptr"></a><a name="ccomptr"></a>CComPtr::CComPtr

El constructor.

```cpp
CComPtr() throw ();
CComPtr(T* lp) throw ();
CComPtr (const CComPtr<T>& lp) throw ();
```

### <a name="parameters"></a>Parámetros

*Lp*<br/>
Se utiliza para inicializar el puntero de interfaz.

*T*<br/>
Una interfaz COM.

### <a name="remarks"></a>Observaciones

Los constructores que toman `AddRef` una llamada de argumento en *lp*, si no es un puntero nulo. Un objeto propiedad no null `Release` obtiene una llamada a la destrucción del objeto CComPtr, o si se asigna un nuevo objeto a la CComPtr objeto.

## <a name="ccomptroperator-"></a><a name="operator_eq"></a>CComPtr::operador ?

Operador de asignación.

```cpp
T* operator= (T* lp) throw ();
T* operator= (const CComPtr<T>& lp) throw ();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero `CComPtr` al objeto actualizado

### <a name="remarks"></a>Observaciones

Esta operación AddRefs el nuevo objeto y libera el objeto existente, si existe.

## <a name="see-also"></a>Consulte también

[CComPtr::CComPtr](#ccomptr)<br/>
[CComQIPtr::CComQIPtr](../../atl/reference/ccomqiptr-class.md#ccomqiptr)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
