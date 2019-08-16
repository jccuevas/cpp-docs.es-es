---
title: conditional (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::conditional
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
ms.openlocfilehash: b8f0f69cc1e4f6966bc9ccb63fe529436295badd
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457319"
---
# <a name="conditional-class"></a>conditional (Clase)

Selecciona uno de dos tipos en función de la condición especificada.

## <a name="syntax"></a>Sintaxis

```cpp
template <bool B, class T1, class T2>
struct conditional;

template <bool _Test, class _T1, class _T2>
using conditional_t = typename conditional<_Test, _T1, _T2>::type;
```

### <a name="parameters"></a>Parámetros

*B*\
Valor que determina el tipo seleccionado.

*T1*\
Resultado del tipo cuando B es true.

*T2*\
Resultado del tipo cuando B es false.

## <a name="remarks"></a>Comentarios

La definición `conditional<B, T1, T2>::type` de tipo de miembro de plantilla se evalúa como *T1* cuando *b* se evalúa como **true**y se evalúa como *T2* cuando *b* se evalúa como **false**.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)
