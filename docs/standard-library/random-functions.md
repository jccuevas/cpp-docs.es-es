---
title: Funciones &lt;random&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
caps.latest.revision: 10
manager: ghogen
ms.openlocfilehash: e3c5dba462b45589005a996e6226330882b29b15
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
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
