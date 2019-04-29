---
title: conditional (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::conditional
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
ms.openlocfilehash: be81a1bc32f2f86f1d79970868933bddb8dc3620
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62212110"
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

*B*<br/>
Valor que determina el tipo seleccionado.

*T1*<br/>
Resultado del tipo cuando B es true.

*T2*<br/>
Resultado del tipo cuando B es false.

## <a name="remarks"></a>Comentarios

El typedef de miembro de plantilla `conditional<B, T1, T2>::type` se evalúa como *T1* cuando *B* se evalúa como **true**y se evalúa como *T2* cuando  *B* se evalúa como **false**.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
