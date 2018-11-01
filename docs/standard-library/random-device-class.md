---
title: random_device (Clase)
ms.date: 11/04/2016
f1_keywords:
- random/std::random_device
- random/std::random_device::min
- random/std::random_device::max
- random/std::random_device::entropy
- random/std::random_device::operator()
helpviewer_keywords:
- std::random_device [C++]
- std::random_device [C++], min
- std::random_device [C++], max
- std::random_device [C++], entropy
- std::random_device [C++], entropy
ms.assetid: 4393d515-0cb6-4e0d-a2ba-c780f05dc1bf
ms.openlocfilehash: 783b8f587094c6d603cc02f41b516ebd7b1e9a08
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580653"
---
# <a name="randomdevice-class"></a>random_device (Clase)

Genera una secuencia aleatoria desde un dispositivo externo.

## <a name="syntax"></a>Sintaxis

```cpp
class random_device {
public:
   typedef unsigned int result_type;

   // constructor
   explicit random_device(const std::string& token = "");

   // properties
   static result_type min();
   static result_type max();
   double entropy() const;

   // generate
   result_type operator()();

   // no-copy functions
   random_device(const random_device&) = delete;
   void operator=(const random_device&) = delete;
   };
```

## <a name="members"></a>Miembros

|||
|-|-|
|[random_device](#random_device)|[Entropía](#entropy)|
|[random_device::operator()](#op_call)||

## <a name="remarks"></a>Comentarios

La clase describe un origen de números aleatorios y puede ser (aunque no es obligatorio) no determinista o segura criptográficamente según la norma ISO C++. En la implementación de Visual Studio, los valores generados son no deterministas y seguros criptográficamente, pero se ejecutan con mayor lentitud que los generadores creados a partir de motores y adaptadores de motor (como el [motor Mersenne Twister](../standard-library/mersenne-twister-engine-class.md), que constituye la opción de motor más rápida y de mejor calidad la mayoría de las veces).

Los resultados de `random_device` se distribuyen uniformemente en el intervalo cerrado [ `0, 2`<sup>32</sup>).

No está garantizado que `random_device` resulte en una llamada de no bloqueo.

`random_device` se suele usar para propagar otros generadores creados con motores o adaptadores de motor. Para obtener más información, vea [\<random>](../standard-library/random.md).

## <a name="example"></a>Ejemplo

En el siguiente código se muestra la funcionalidad básica de esta clase y resultados de ejemplo. Dada la naturaleza no determinista de `random_device`, los valores aleatorios que aparecen en la sección **Resultado** no coincidirán con los suyos. Esto es normal y lo que se espera.

```cpp
// random_device_engine.cpp
// cl.exe /W4 /nologo /EHsc /MTd
#include <random>
#include <iostream>
using namespace std;

int main()
{
    random_device gen;

    cout << "entropy == " << gen.entropy() << endl;
    cout << "min == " << gen.min() << endl;
    cout << "max == " << gen.max() << endl;

    cout << "a random value == " << gen() << endl;
    cout << "a random value == " << gen() << endl;
    cout << "a random value == " << gen() << endl;
}
```

```Output
entropy == 32
min == 0
max == 4294967295
a random value == 2378414971
a random value == 3633694716
a random value == 213725214
```

Este ejemplo es simplista y no representa el caso de uso general de este generador. Para obtener un código de ejemplo representativo, vea [\<random>](../standard-library/random.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** \<random>

**Espacio de nombres:** std

## <a name="random_device"></a> random_device::random_device

Construye el generador.

```cpp
random_device(const std::string& = "");
```

### <a name="remarks"></a>Comentarios

El constructor inicializa el generador según sea necesario, omitiendo el parámetro de cadena. Genera un valor de un tipo definido en la implementación que se deriva de una [excepción](../standard-library/exception-class.md) si `random_device` no se pudo inicializar.

## <a name="entropy"></a> random_device::entropy

Estima la aleatoriedad del origen.

```cpp
double entropy() const noexcept;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve una estimación de la aleatoriedad del origen, medida en bits.

## <a name="op_call"></a> random_device::operator()

Devuelve un valor aleatorio.

```cpp
result_type operator()();
```

### <a name="remarks"></a>Comentarios

Devuelve valores distribuidos uniformemente en el intervalo cerrado [`min, max`] como lo determinan las funciones miembro `min()` y `max()`. Inicia un valor de un tipo definido por la implementación derivado de la [excepción](../standard-library/exception-class.md) si no se ha podido obtener un número aleatorio.

## <a name="see-also"></a>Vea también

[\<random>](../standard-library/random.md)<br/>
