---
title: Casttobase (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToBase
dev_langs:
- C++
helpviewer_keywords:
- CastToBase method
ms.assetid: 0591a017-0adf-4358-b946-eb0a307ce7f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 55a4d7487be5b3565ba3945630cab4388f287a68
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611829"
---
# <a name="interfacetraitscasttobase-method"></a>InterfaceTraits::CastToBase (Método)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename T>
static __forceinline Base* CastToBase(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Parámetros

*T*  
El tipo de parámetro *ptr*.

*ptr*  
Puntero a un tipo *T*.

## <a name="return-value"></a>Valor devuelto

Un puntero a `Base`.

## <a name="remarks"></a>Comentarios

Convierte el puntero especificado a un puntero a `Base`.

Para obtener más información acerca de `Base`, vea la sección de definiciones de tipo público en [InterfaceTraits (estructura)](../windows/interfacetraits-structure.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[InterfaceTraits (estructura)](../windows/interfacetraits-structure.md)  
[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)