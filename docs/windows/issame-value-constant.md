---
title: Issame constante | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsSame::value
dev_langs:
- C++
helpviewer_keywords:
- value constant
ms.assetid: ee72deff-54a2-4482-9967-49a86d07f834
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f1f67769f7bab517c6a5010788c3627529f14db2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373527"
---
# <a name="issamevalue-constant"></a>IsSame::value (Constante)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename T1, typename T2>
struct IsSame
{
    static const bool value = false;
};

template <typename T1>
struct IsSame<T1, T1>
{
    static const bool value = true;
};
```

## <a name="remarks"></a>Comentarios

Indica si un tipo es igual a otro.

**valor** es **true** si los parámetros de plantilla son los mismos, y **false** si los parámetros de plantilla son diferentes.

## <a name="requirements"></a>Requisitos

**Encabezado:** internal.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[IsSame (estructura)](../windows/issame-structure.md)<br/>
[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)