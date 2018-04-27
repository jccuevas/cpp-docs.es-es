---
title: Clase linear_congruential_engine | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- random/std::linear_congruential_engine
dev_langs:
- C++
helpviewer_keywords:
- linear_congruential_engine class
ms.assetid: 30e00ca6-1933-4701-9561-54f3e810a5a1
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 85af6002d769f7d817c05bbe8433bb4cb8381828
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="linearcongruentialengine-class"></a>linear_congruential_engine (Clase)

Genera una secuencia aleatoria mediante un algoritmo congruencial lineal.

## <a name="syntax"></a>Sintaxis

```cpp
class linear_congruential_engine{
   public:  // types
   typedef UIntType result_type;
   // engine characteristics
   static constexpr result_type multiplier = a;
   static constexpr result_type increment = c;
   static constexpr result_type modulus = m;
   static constexpr result_type min() { return c == 0u  1u: 0u; }
   static constexpr result_type max() { return m - 1u; }
   static constexpr result_type default_seed = 1u;
   // constructors and seeding functions
   explicit linear_congruential_engine(result_type s = default_seed);
   template <class Sseq>
   explicit linear_congruential_engine(Sseq& q);
   void seed(result_type s = default_seed);
   template <class Sseq>
   void seed(Sseq& q);
   // generating functions
   result_type operator()();
   void discard(unsigned long long z);
   };
```

### <a name="parameters"></a>Parámetros

`UIntType` El tipo de resultado entero sin signo. Para obtener información sobre los tipos posibles, vea [\<random>](../standard-library/random.md).

`A` **Multiplicador**. **Condición previa**: vea la sección Comentarios.

`C` **Incremento**. **Condición previa**: vea la sección Comentarios.

`M` **Módulo**. **Condición previa**: vea los comentarios.

## <a name="members"></a>Miembros

||||
|-|-|-|
|`linear_congruential_engine::linear_congruential_engine`|`linear_congruential_engine::min`|`linear_congruential_engine::discard`|
|`linear_congruential_engine::operator()`|`linear_congruential_engine::max`|`linear_congruential_engine::seed`|

`default_seed` es un miembro constante, definido como `1u`, utilizado como el valor de parámetro predeterminado para `linear_congruential_engine::seed` y el constructor de valores simple.

Para obtener más información sobre los miembros del motor, vea [\<random>](../standard-library/random.md).

## <a name="remarks"></a>Comentarios

La clase de plantilla `linear_congruential_engine` es el motor de generador más sencillo, pero no el más rápido ni de mejor calidad. Una mejora realizada sobre este motor es el [motor de resta llevando](../standard-library/subtract-with-carry-engine-class.md). Ninguno de estos motores logra unos resultados tan rápidos y de tan alta calidad como el [motor Mersenne Twister](../standard-library/mersenne-twister-engine-class.md).

Este motor genera valores de un tipo integral sin signo especificado por el usuario mediante la relación de repetición (*período*) `x(i) = (A * x(i-1) + C) mod M`.

Si `M` es cero, el valor usado en esta operación de módulo es `numeric_limits<result_type>::max() + 1`. El estado del motor es el último valor devuelto, o bien el valor de inicialización si no se ha llamado a `operator()`.

Si `M` no es cero, los valores de los argumentos de plantilla `A` y `C` deben ser inferiores a `M`.

Aunque puede construir un generador directamente a partir de este motor, también puede usar una de estas definiciones de tipo predefinidas.

`minstd_rand0`: motor estándar mínimo 1988 (Lewis, Goodman y Miller, 1969).

```cpp
typedef linear_congruential_engine<unsigned int, 16807, 0, 2147483647> minstd_rand0;
```

`minstd_rand`: Motor estándar mínimo `minstd_rand0` actualizado (Park, Miller y Stockmeyer, 1993).

```cpp
typedef linear_congruential_engine<unsigned int, 48271, 0, 2147483647> minstd_rand;
```

Para obtener más información sobre el algoritmo de motor congruencial lineal, vea el artículo de la Wikipedia sobre el [generador congruencial lineal](http://go.microsoft.com/fwlink/p/?linkid=402446).

## <a name="requirements"></a>Requisitos

**Encabezado:** \<random>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[\<random>](../standard-library/random.md)<br/>
