---
title: conditional (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- type_traits/std::conditional
dev_langs:
- C++
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 40d7e873ce7ae5814423d4b5e3899ef8bbb46fa7
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
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

`B` El valor que determina el tipo seleccionado.

`T1` El resultado de tipo cuando B es true.

`T2` El resultado de tipo cuando B es false.

## <a name="remarks"></a>Comentarios

La definición de tipo de miembro de plantilla `conditional<B, T1, T2>::type` se evalúa como `T1` cuando `B` se evalúa como `true`, y se evalúa como `T2` cuando `B` se evalúa como `false`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
