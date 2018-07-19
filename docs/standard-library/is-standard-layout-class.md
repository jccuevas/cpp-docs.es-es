---
title: Clase is_standard_layout | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_standard_layout
dev_langs:
- C++
helpviewer_keywords:
- is_standard_layout class
- is_standard_layout
ms.assetid: 15ccf111-f537-45ef-b552-59152a7ba312
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6223151acbce299178101735db05f7b4bd516f2f
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965518"
---
# <a name="isstandardlayout-class"></a>is_standard_layout (Clase)

Comprueba si el tipo es un diseño estándar.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct is_standard_layout;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Ty*|El tipo que se va a consultar.|

## <a name="remarks"></a>Comentarios

Una instancia de este predicado de tipo contiene true si el tipo *Ty* es una clase que tiene un diseño estándar de objetos miembro en la memoria, en caso contrario, es false.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
