---
title: InterfaceTraits (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits
dev_langs:
- C++
helpviewer_keywords:
- InterfaceTraits structure
ms.assetid: ede0c284-19a7-4892-9738-ff3da4923d0a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cb8eb8fbc4199ccdaf5717e465f202c0e4ec296e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46437658"
---
# <a name="interfacetraits-structure"></a>InterfaceTraits (estructura)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template<
   typename I0
>
struct __declspec(novtable) InterfaceTraits;
template<typename CloakedType>
struct __declspec(novtable) InterfaceTraits<CloakedIid<CloakedType>>;

template<>
struct __declspec(novtable) InterfaceTraits<Nil>;
```

### <a name="parameters"></a>Parámetros

*I0*<br/>
El nombre de una interfaz.

*CloakedType*<br/>
Para `RuntimeClass`, `Implements` y `ChainInterfaces`, admite la interfaz que no estará en la lista de identificadores de interfaz.

## <a name="remarks"></a>Comentarios

Características comunes de implementa de una interfaz.

La segunda plantilla es una especialización para interfaces encubiertas. La tercera plantilla es una especialización para parámetros Nil.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|`Base`|Un sinónimo para el *I0* parámetro de plantilla.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[InterfaceTraits::CanCastTo (método)](../windows/interfacetraits-cancastto-method.md)|Indica si el puntero especificado se puede convertir en un puntero a `Base`.|
|[InterfaceTraits::CastToBase (método)](../windows/interfacetraits-casttobase-method.md)|Convierte el puntero especificado a un puntero a `Base`.|
|[InterfaceTraits::CastToUnknown (método)](../windows/interfacetraits-casttounknown-method.md)|Convierte el puntero especificado a un puntero a `IUnknown`.|
|[InterfaceTraits::FillArrayWithIid (método)](../windows/interfacetraits-fillarraywithiid-method.md)|Asigna el identificador de interfaz de `Base` al elemento de matriz especificado por el argumento de índice.|
|[InterfaceTraits::Verify (método)](../windows/interfacetraits-verify-method.md)|Comprueba que `Base` se deriva correctamente.|

### <a name="public-constants"></a>Constantes públicas

|nombre|Descripción|
|----------|-----------------|
|[InterfaceTraits::IidCount (constante)](../windows/interfacetraits-iidcount-constant.md)|Contiene el número de identificadores asociados con la actual interfaz **InterfaceTraits** objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`InterfaceTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)