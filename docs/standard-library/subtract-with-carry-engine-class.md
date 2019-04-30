---
title: subtract_with_carry_engine (Clase)
ms.date: 11/04/2016
f1_keywords:
- random/std::subtract_with_carry_engine
- random/std::subtract_with_carry_engine::default_seed
- random/std::subtract_with_carry_engine::discard
- random/std::subtract_with_carry_engine::min
- random/std::subtract_with_carry_engine::max
- random/std::subtract_with_carry_engine::seed
helpviewer_keywords:
- std::subtract_with_carry_engine [C++]
- std::subtract_with_carry_engine [C++], default_seed
- std::subtract_with_carry_engine [C++], discard
- std::subtract_with_carry_engine [C++], min
- std::subtract_with_carry_engine [C++], max
- std::subtract_with_carry_engine [C++], seed
ms.assetid: 94a055f2-a620-4a22-ac34-c156924bab31
ms.openlocfilehash: 76981df1f4a642cca1a57a9619f20aa4cebd63bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412196"
---
# <a name="subtractwithcarryengine-class"></a>subtract_with_carry_engine (Clase)

Genera una secuencia aleatoria mediante el algoritmo resta por acarreo (Fibonacci retrasado).

## <a name="syntax"></a>Sintaxis

```cpp
template <class UIntType, size_t W, size_t S, size_t R>
class subtract_with_carry_engine;
```

### <a name="parameters"></a>Parámetros

*UIntType*<br/>
El tipo de resultado integral sin signo. Para obtener información sobre los tipos posibles, vea [\<random>](../standard-library/random.md).

*W*<br/>
**Tamaño de palabra**. Tamaño de cada palabra, en bits, de la secuencia de estado. **Condición previa:** `0 < W ≤ numeric_limits<UIntType>::digits`

*S*<br/>
**Intervalo corto**. Número de valores íntegros. **Condición previa:** `0 < S < R`

*R*<br/>
**Intervalo largo**. Determina la recurrencia en la serie generada.

## <a name="members"></a>Miembros

||||
|-|-|-|
|`subtract_with_carry_engine::subtract_with_carry_engine`|`subtract_with_carry_engine::min`|`subtract_with_carry_engine::discard`|
|`subtract_with_carry_engine::operator()`|`subtract_with_carry_engine::max`|`subtract_with_carry_engine::seed`|
|`default_seed` es un miembro constante, definido como `19780503u`, utilizado como el valor de parámetro predeterminado para `subtract_with_carry_engine::seed` y el constructor de valores simple.|||

Para obtener más información sobre los miembros del motor, vea [\<random>](../standard-library/random.md).

## <a name="remarks"></a>Comentarios

La clase de plantilla `substract_with_carry_engine` es una mejora respecto al [linear_congruential_engine](../standard-library/linear-congruential-engine-class.md). Ninguno de estos motores es tan rápido o tiene unos resultados de mayor calidad que el [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md).

Este motor produce valores de un tipo entero sin signo especificado por el usuario que usa la relación de periodicidad ( *periodo*) `x(i) = (x(i - R) - x(i - S) - cy(i - 1)) mod M`, en la que `cy(i)` tiene el valor `1` si `x(i - S) - x(i - R) - cy(i - 1) < 0`. De lo contrario `0`, y `M` tiene el valor `2`<sup>W</sup>. El estado del motor es un carry de indicador de signo más *R* valores. Estos valores consisten en los últimos *R* valores que se devuelve si `operator()` se ha llamado al menos *R* agota el tiempo, en caso contrario, el `N` valores que se han devuelto y los últimos `R - N` valores de la inicialización.

El argumento de la plantilla `UIntType` debe ser lo suficientemente grande para contener valores de hasta `M - 1`.

Aunque puede construir un generador directamente a partir de este motor, también puede usar una de estas definiciones de tipos predefinidas:

`ranlux24_base`: Utilizado como base para `ranlux24`.
`typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;`

`ranlux48_base`: Utilizado como base para `ranlux48`.
`typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;`

Para más detalles sobre el algoritmo de motor de resta con llevadas, vea el artículo de la Wikipedia sobre el [generador de Fibonacci retardado](https://en.wikipedia.org/wiki/Lagged_Fibonacci_generator).

## <a name="requirements"></a>Requisitos

**Encabezado:** \<random>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[\<random>](../standard-library/random.md)<br/>
