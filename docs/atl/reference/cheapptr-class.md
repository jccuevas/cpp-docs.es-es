---
title: CHeapPtr (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CHeapPtr
- ATLCORE/ATL::CHeapPtr
- ATLCORE/ATL::CHeapPtr::CHeapPtr
- ATLCORE/ATL::CHeapPtr::Allocate
- ATLCORE/ATL::CHeapPtr::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CHeapPtr class
ms.assetid: e5c5bfd4-9bf1-4164-8a83-8155fe253454
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34a6b019c2e3f71b70253ad2c15bc4b2758eeae7
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762085"
---
# <a name="cheapptr-class"></a>CHeapPtr (clase)

Una clase de puntero inteligente para administrar los punteros de montón.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template<typename T, class Allocator=CCRTAllocator>  
class CHeapPtr : public CHeapPtrBase<T, Allocator>
```

#### <a name="parameters"></a>Parámetros

*T*  
El tipo de objeto que se almacenará en el montón.

*Asignador*  
La clase de asignación de memoria que utilice.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CHeapPtr::CHeapPtr](#cheapptr)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CHeapPtr::Allocate](#allocate)|Llame a este método para asignar memoria del montón para almacenar objetos.|
|[CHeapPtr::Reallocate](#reallocate)|Llame a este método para volver a asignar la memoria del montón.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CHeapPtr::operator =](#operator_eq)|El operador de asignación.|

## <a name="remarks"></a>Comentarios

`CHeapPtr` se deriva de [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) y de forma predeterminada, usa las rutinas de CRT (en [CCRTAllocator](../../atl/reference/ccrtallocator-class.md)) para asignar y liberar memoria. La clase [CHeapPtrList](../../atl/reference/cheapptrlist-class.md) puede usarse para construir una lista de punteros del montón. Vea también [CComHeapPtr](../../atl/reference/ccomheapptr-class.md), que utiliza rutinas de asignación de memoria COM.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)

`CHeapPtr`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcore.h

##  <a name="allocate"></a>  CHeapPtr::Allocate

Llame a este método para asignar memoria del montón para almacenar objetos.

```
bool Allocate(size_t nElements = 1) throw();
```

### <a name="parameters"></a>Parámetros

*nElements*  
El número de elementos que se usan para calcular la cantidad de memoria para asignar. El valor predeterminado es 1.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la memoria se correctamente asignada, false en caso de error.

### <a name="remarks"></a>Comentarios

Las rutinas de asignador sirven para reservar memoria suficiente en el montón para almacenar *nElement* objetos de un tipo definido en el constructor.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#77](../../atl/codesnippet/cpp/cheapptr-class_1.cpp)]

##  <a name="cheapptr"></a>  CHeapPtr::CHeapPtr

El constructor.

```
CHeapPtr() throw();
explicit CHeapPtr(T* p) throw();
CHeapPtr(CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>Parámetros

*p*  
Un puntero de montón existente o `CHeapPtr`.

### <a name="remarks"></a>Comentarios

El puntero del montón, opcionalmente, puede crearse mediante un puntero existente, o un `CHeapPtr` objeto. Si es así, el nuevo `CHeapPtr` objeto asume la responsabilidad de administrar los recursos y el nuevo puntero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#78](../../atl/codesnippet/cpp/cheapptr-class_2.cpp)]

##  <a name="operator_eq"></a>  CHeapPtr::operator =

Operador de asignación.

```
CHeapPtr<T, Allocator>& operator=(
    CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>Parámetros

*p*  
Objeto `CHeapPtr` existente.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia a la actualización `CHeapPtr`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#80](../../atl/codesnippet/cpp/cheapptr-class_3.cpp)]

##  <a name="reallocate"></a>  CHeapPtr::Reallocate

Llame a este método para volver a asignar la memoria del montón.

```
bool Reallocate(size_t nElements) throw();
```

### <a name="parameters"></a>Parámetros

*nElements*  
El nuevo número de elementos que se usan para calcular la cantidad de memoria para asignar.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la memoria se correctamente asignada, false en caso de error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#79](../../atl/codesnippet/cpp/cheapptr-class_4.cpp)]

## <a name="see-also"></a>Vea también

[CHeapPtrBase (clase)](../../atl/reference/cheapptrbase-class.md)   
[CCRTAllocator (clase)](../../atl/reference/ccrtallocator-class.md)   
[Información general de clases](../../atl/atl-class-overview.md)
