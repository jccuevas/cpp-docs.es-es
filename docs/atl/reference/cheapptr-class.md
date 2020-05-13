---
title: Clase CHeapPtr
ms.date: 11/04/2016
f1_keywords:
- CHeapPtr
- ATLCORE/ATL::CHeapPtr
- ATLCORE/ATL::CHeapPtr::CHeapPtr
- ATLCORE/ATL::CHeapPtr::Allocate
- ATLCORE/ATL::CHeapPtr::Reallocate
helpviewer_keywords:
- CHeapPtr class
ms.assetid: e5c5bfd4-9bf1-4164-8a83-8155fe253454
ms.openlocfilehash: a512aa974cb57072915f887f0c2a20ed1263ffa3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326915"
---
# <a name="cheapptr-class"></a>Clase CHeapPtr

Una clase de puntero inteligente para administrar punteros de montón.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<typename T, class Allocator=CCRTAllocator>
class CHeapPtr : public CHeapPtrBase<T, Allocator>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de objeto que se va a almacenar en el montón.

*Asignador*<br/>
La clase de asignación de memoria que se va a utilizar.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CheapPtr::CheapPtr](#cheapptr)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHeapPtr::Asignar](#allocate)|Llame a este método para asignar memoria en el montón para almacenar objetos.|
|[CHeapPtr::Reallocate](#reallocate)|Llame a este método para reasignar la memoria en el montón.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHeapPtr::operador ?](#operator_eq)|El operador de asignación.|

## <a name="remarks"></a>Observaciones

`CHeapPtr`se deriva de [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) y de forma predeterminada utiliza las rutinas de CRT (en [CCRTAllocator](../../atl/reference/ccrtallocator-class.md)) para asignar y liberar memoria. La clase [CHeapPtrList](../../atl/reference/cheapptrlist-class.md) se puede utilizar para construir una lista de punteros de montón. Consulte también [CComHeapPtr](../../atl/reference/ccomheapptr-class.md), que utiliza rutinas de asignación de memoria COM.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)

`CHeapPtr`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcore.h

## <a name="cheapptrallocate"></a><a name="allocate"></a>CHeapPtr::Asignar

Llame a este método para asignar memoria en el montón para almacenar objetos.

```
bool Allocate(size_t nElements = 1) throw();
```

### <a name="parameters"></a>Parámetros

*nElementos*<br/>
El número de elementos utilizados para calcular la cantidad de memoria que se va a asignar. El valor predeterminado es 1.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la memoria se asignó correctamente, false en caso de error.

### <a name="remarks"></a>Observaciones

Las rutinas de asignador se utilizan para reservar suficiente memoria en el montón para almacenar *nElement* objetos de un tipo definido en el constructor.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#77](../../atl/codesnippet/cpp/cheapptr-class_1.cpp)]

## <a name="cheapptrcheapptr"></a><a name="cheapptr"></a>CheapPtr::CheapPtr

El constructor.

```
CHeapPtr() throw();
explicit CHeapPtr(T* p) throw();
CHeapPtr(CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
Un puntero de `CHeapPtr`montón existente o .

### <a name="remarks"></a>Observaciones

El puntero de montón se puede crear `CHeapPtr` opcionalmente mediante un puntero existente o un objeto. Si es así, el nuevo `CHeapPtr` objeto asume la responsabilidad de administrar el nuevo puntero y los recursos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#78](../../atl/codesnippet/cpp/cheapptr-class_2.cpp)]

## <a name="cheapptroperator-"></a><a name="operator_eq"></a>CHeapPtr::operador ?

Operador de asignación.

```
CHeapPtr<T, Allocator>& operator=(
    CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
Objeto `CHeapPtr` existente.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia `CHeapPtr`al archivo .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#80](../../atl/codesnippet/cpp/cheapptr-class_3.cpp)]

## <a name="cheapptrreallocate"></a><a name="reallocate"></a>CHeapPtr::Reallocate

Llame a este método para reasignar la memoria en el montón.

```
bool Reallocate(size_t nElements) throw();
```

### <a name="parameters"></a>Parámetros

*nElementos*<br/>
El nuevo número de elementos utilizados para calcular la cantidad de memoria que se va a asignar.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la memoria se asignó correctamente, false en caso de error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#79](../../atl/codesnippet/cpp/cheapptr-class_4.cpp)]

## <a name="see-also"></a>Consulte también

[Clase CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)<br/>
[Clase CCRTAllocator](../../atl/reference/ccrtallocator-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
