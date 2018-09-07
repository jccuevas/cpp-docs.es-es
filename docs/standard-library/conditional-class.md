---
title: conditional (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::conditional
dev_langs:
- C++
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a553c2975dd5a58673bd4caa6e7c9ba25d33183
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44106618"
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
