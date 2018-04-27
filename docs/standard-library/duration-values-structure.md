---
title: duration_values (Estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- chrono/std::chrono::duration_values
- chrono/std::chrono::duration_values::max
- chrono/std::chrono::duration_values::min
- chrono/std::chrono::duration_values::zero
dev_langs:
- C++
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a2cba8fd6fe3e4763e05dc0cc897e8a0b968d611
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="durationvalues-structure"></a>duration_values (Estructura)

Proporciona valores concretos para el parámetro de plantilla [duration](../standard-library/duration-class.md) `Rep`.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Rep>
struct duration_values;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[max](#max)|Estático. Especifica el límite superior para un valor de tipo `Rep`.|
|[min](#min)|Estático. Especifica el límite inferior para un valor de tipo `Rep`.|
|[Cero](#zero)|Estático. Devuelve `Rep(0)`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<chrono >

**Espacio de nombres:** std::chrono

## <a name="max"></a>  duration_values::max

Método estático que devuelve el límite superior para los valores de tipo `Ref`.

```cpp
static constexpr Rep max();
```

### <a name="return-value"></a>Valor devuelto

En efecto, devuelve `numeric_limits<Rep>::max()`.

### <a name="remarks"></a>Comentarios

Cuando `Rep` es un tipo definido por el usuario, el valor devuelto debe ser mayor que [duration_values::zero](#zero).

## <a name="min"></a>  duration_values::min

Método estático que devuelve el límite inferior para valores de tipo `Ref`.

```cpp
static constexpr Rep min();
```

### <a name="return-value"></a>Valor devuelto

En efecto, devuelve `numeric_limits<Rep>::lowest()`.

### <a name="remarks"></a>Comentarios

Cuando `Rep` es un tipo definido por el usuario, el valor devuelto debe ser menor o igual que [duration_values::zero](#zero).

## <a name="zero"></a>  duration_values::zero

Devuelve `Rep(0)`.

```cpp
static constexpr Rep zero();
```

### <a name="remarks"></a>Comentarios

Cuando `Rep` es un tipo definido por el usuario, el valor devuelto debe representar el infinito aditivo.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
