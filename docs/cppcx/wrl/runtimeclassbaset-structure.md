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
ms.openlocfilehash: 06a9f73e00d541b0e5bcbe20c57befe4a67c5132
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375720"
---
# <a name="runtimeclassbaset-structure"></a>RuntimeClassBaseT (Estructura)

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <unsigned int RuntimeClassTypeT>
friend struct Details::RuntimeClassBaseT;
```

### <a name="parameters"></a>Parámetros

*RuntimeClassTypeT*<br/>
Campo de indicadores que especifica uno o varios enumeradores [RuntimeClassType.](runtimeclasstype-enumeration.md)

## <a name="remarks"></a>Observaciones

Proporciona métodos `QueryInterface` auxiliares para las operaciones y la obtención de iDs de interfaz.

## <a name="members"></a>Miembros

### <a name="protected-methods"></a>Métodos protegidos

Nombre                                                         | Descripción
------------------------------------------------------------ | -----------------------------------------------------------------------------
[RuntimeClassBaseT::AsIID](#asiid)                           | Recupera un puntero al identificador de interfaz especificado.
[RuntimeClassBaseT::GetImplementedIIDS](#getimplementediids) | Recupera una matriz de iDs de interfaz que se implementan mediante un tipo especificado.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`RuntimeClassBaseT`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL::Details

## <a name="runtimeclassbasetasiid"></a><a name="asiid"></a>RuntimeClassBaseT::AsIID

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

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
Tipo que implementa el identificador de interfaz especificado por el parámetro *riid*.

*implementa*<br/>
Variable del tipo especificado por el parámetro de plantilla *T*.

*riid*<br/>
El ID de interfaz que se va a recuperar.

*ppvObject*<br/>
Si esta operación se realiza correctamente, un puntero a un puntero a la interfaz especificada por el parámetro *riid*.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error.

### <a name="remarks"></a>Observaciones

Recupera un puntero al identificador de interfaz especificado.

## <a name="runtimeclassbasetgetimplementediids"></a><a name="getimplementediids"></a>RuntimeClassBaseT::GetImplementedIIDS

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

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
El tipo del parámetro *implements.*

*implementa*<br/>
Puntero al tipo especificado por el parámetro *T*.

*iidCount*<br/>
El número máximo de interfaces que se van a recuperar.

*iids*<br/>
Si esta operación se completa correctamente, una matriz de los iD de interfaz implementada por el tipo *T*.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error.

### <a name="remarks"></a>Observaciones

Recupera una matriz de iDs de interfaz que se implementan mediante un tipo especificado.
