---
title: Funciones &lt;random&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: c8ee20759e66c7beb295de96b8311df46555ac6b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="ltrandomgt-functions"></a>Funciones &lt;random&gt;

## <a name="generate_canonical"></a> generate_canonical

Especifica un valor de punto flotante de una secuencia aleatoria.

> [!NOTE]
> La norma ISO C++ indica que esta función debe devolver valores dentro del intervalo [ `0`, `1`). Visual Studio todavía no cumple plenamente esta limitación. Use [uniform_real_distribution](../standard-library/uniform-real-distribution-class.md) como solución provisional para generar valores en este intervalo.

```cpp
template <class RealType, size_t Bits, class Generator>
RealType generate_canonical(Generator& Gen);
```

### <a name="parameters"></a>Parámetros

`RealType` Tipo integral de punto flotante. Para obtener información sobre los tipos posibles, vea [\<random>](../standard-library/random.md).

`Bits` El generador de números aleatorios.

`Gen` El generador de números aleatorios.

### <a name="remarks"></a>Comentarios

La función de plantilla llama a `operator()` de `Gen` repetidas veces y empaqueta los valores devueltos en un valor de punto flotante `x` de tipo `RealType` hasta reunir el número especificado de bits de mantisa en `x`. El número especificado es el más pequeño de `Bits` (que no debe ser cero) y el número completo de bits de mantisa en `RealType`. La primera llamada proporciona los bits de orden más bajo. La función devuelve `x`.

## <a name="see-also"></a>Vea también

[\<random>](../standard-library/random.md)<br/>
