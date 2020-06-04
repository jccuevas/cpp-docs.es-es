---
title: _com_ptr_t::Release
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t.Release
- _com_ptr_t::Release
helpviewer_keywords:
- Release method [C++]
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
ms.openlocfilehash: 73de3c2d19063f0738b8b0a3c510ea520f58de0b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745056"
---
# <a name="_com_ptr_trelease"></a>_com_ptr_t::Release

**Microsoft Specific**

Llama **Release** a la `IUnknown` función miembro Release de en el puntero de interfaz encapsulado.

## <a name="syntax"></a>Sintaxis

```cpp
void Release( );
```

## <a name="remarks"></a>Observaciones

Llama `IUnknown::Release` al puntero de interfaz `E_POINTER` encapsulado, generando un error si este puntero de interfaz es NULL.

**END Microsoft Specific**

## <a name="see-also"></a>Vea también

[Clase _com_ptr_t](../cpp/com-ptr-t-class.md)
