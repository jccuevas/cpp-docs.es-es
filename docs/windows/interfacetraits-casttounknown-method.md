---
title: Método Interfacetraits | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToUnknown
dev_langs:
- C++
helpviewer_keywords:
- CastToUnknown method
ms.assetid: aca47fa0-3c60-47f2-a73c-258f7160adff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c75e02136c626d72215a2af79d1391863e9f494c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382667"
---
# <a name="interfacetraitscasttounknown-method"></a>InterfaceTraits::CastToUnknown (Método)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename T>
static __forceinline IUnknown* CastToUnknown(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de parámetro *ptr*.

*ptr*<br/>
Puntero al tipo *T*.

## <a name="return-value"></a>Valor devuelto

Puntero a la interfaz IUnknown del que `Base` derivada.

## <a name="remarks"></a>Comentarios

Convierte el puntero especificado a un puntero a `IUnknown`.

Para obtener más información acerca de `Base`, vea la sección de definiciones de tipo público en [InterfaceTraits (estructura)](../windows/interfacetraits-structure.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[InterfaceTraits (estructura)](../windows/interfacetraits-structure.md)<br/>
[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)