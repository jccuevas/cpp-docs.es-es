---
title: RuntimeClassBaseT (Estructura)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::AsIID
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS
helpviewer_keywords:
- Microsoft::WRL::Details::RuntimeClassBaseT structure
- Microsoft::WRL::Details::RuntimeClassBaseT::AsIID method
- Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS method
ms.assetid: a62775fb-3359-4f45-9ff1-c07fa8da464b
ms.openlocfilehash: 3dd55c322e7da3be3f888c4faa88172fd0c17672
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456854"
---
# <a name="runtimeclassbaset-structure"></a>RuntimeClassBaseT (Estructura)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <unsigned int RuntimeClassTypeT>
friend struct Details::RuntimeClassBaseT;
```

### <a name="parameters"></a>Parámetros

*RuntimeClassTypeT*<br/>
Un campo de marcas que especifica uno o más [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) enumeradores.

## <a name="remarks"></a>Comentarios

Proporciona métodos auxiliares para `QueryInterface` operaciones y obtener los identificadores de interfaz.

## <a name="members"></a>Miembros

### <a name="protected-methods"></a>Métodos protegidos

Name                                                         | Descripción
------------------------------------------------------------ | -----------------------------------------------------------------------------
[Runtimeclassbaset](#asiid)                           | Recupera un puntero al identificador de interfaz especificado.
[Runtimeclassbaset](#getimplementediids) | Recupera una matriz de identificadores que se implementan mediante un tipo especificado de interfaz.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`RuntimeClassBaseT`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Namespace:** wrl

## <a name="asiid"></a>Runtimeclassbaset

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
template<typename T>
__forceinline static HRESULT AsIID(
   _In_ T* implements,
   REFIID riid,
   _Deref_out_ void **ppvObject
);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Un tipo que implementa el identificador de interfaz especificado por el parámetro *riid*.

*implements*<br/>
Una variable del tipo especificado por el parámetro de plantilla *T*.

*riid*<br/>
Para recuperar el identificador de interfaz.

*ppvObject*<br/>
Si esta operación se realiza correctamente, un puntero a una de puntero a la interfaz especificada por el parámetro *riid*.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, un valor HRESULT que describe el error.

### <a name="remarks"></a>Comentarios

Recupera un puntero al identificador de interfaz especificado.

## <a name="getimplementediids"></a>Runtimeclassbaset

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
template<typename T>
__forceinline static HRESULT GetImplementedIIDS(
   _In_ T* implements,
   _Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids
);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de la *implementa* parámetro.

*implements*<br/>
Puntero al tipo especificado por el parámetro *T*.

*iidCount*<br/>
El número máximo de identificadores de interfaz para recuperar.

*IID*<br/>
Si esta operación completa correctamente, una matriz de la interfaz implementadas por el tipo de identificadores *T*.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, un valor HRESULT que describe el error.

### <a name="remarks"></a>Comentarios

Recupera una matriz de identificadores que se implementan mediante un tipo especificado de interfaz.
