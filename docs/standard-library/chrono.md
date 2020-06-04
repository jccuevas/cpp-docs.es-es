---
title: '&lt;chrono&gt;'
ms.date: 05/07/2019
f1_keywords:
- chrono/std::chrono::nanoseconds
- chrono/std::chrono::minutes
- chrono/std::chrono::seconds
- <chrono>
- chrono/std::chrono::hours
- chrono/std::chrono::milliseconds
- chrono/std::chrono::microseconds
ms.assetid: 844de749-f306-482e-89bc-6f53c99c8324
ms.openlocfilehash: e27ff146c75da6e90e6336106beba714dbe7c8a8
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689878"
---
# <a name="ltchronogt"></a>&lt;chrono&gt;

Incluya el encabezado estándar \<chrono> para definir las clases y funciones que representan y manipulan las duraciones de tiempo e instantes de tiempo.

A partir de Visual Studio 2015, la implementación de `steady_clock` ha cambiado para cumplir C++ con los requisitos estándar para el desarrollo y la monotónica. `steady_clock` ahora se basa en QueryPerformanceCounter() y `high_resolution_clock` ahora es un typedef para `steady_clock`. Como resultado, en el compilador de Microsoft C++ `steady_clock::time_point` es ahora un typedef para `chrono::time_point<steady_clock>`; sin embargo, esta regla no es necesariamente el caso de otras implementaciones.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<chrono >

**Espacio de nombres:** std

## <a name="members"></a>Miembros

### <a name="classes"></a>Clases

|||
|-|-|
|[duration (Clase)](../standard-library/duration-class.md)|Describe un tipo que contenga un intervalo de tiempo.|
|[time_point (Clase)](../standard-library/time-point-class.md)|Describe un tipo que representa un punto en el tiempo.|

### <a name="structs"></a>Structs

|||
|-|-|
|[common_type (Estructura)](../standard-library/common-type-structure.md)|Describe las especializaciones de la plantilla de clase [common_type](../standard-library/common-type-class.md) para las creaciones de instancias de `duration` y `time_point`.|
|[duration_values (Estructura)](../standard-library/duration-values-structure.md)|Proporciona valores concretos para el parámetro `Rep` de plantilla `duration`.|
|[struct high_resolution_clock](../standard-library/high-resolution-clock-struct.md)||
|[steady_clock (struct)](../standard-library/steady-clock-struct.md)|Representa un reloj `steady`.|
|[system_clock (Estructura)](../standard-library/system-clock-structure.md)|Representa un *tipo de reloj* basado en el reloj en tiempo real del sistema.|
|[treat_as_floating_point (Estructura)](../standard-library/treat-as-floating-point-structure.md)|Especifica si un tipo puede tratarse como un tipo de punto flotante.|

### <a name="functions"></a>Funciones

|||
|-|-|
|[duration_cast](../standard-library/chrono-functions.md#duration_cast)|Convierte un objeto `duration` a un tipo especificado.|
|[time_point_cast](../standard-library/chrono-functions.md#time_point_cast)|Convierte un objeto `time_point` a un tipo especificado.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator-](../standard-library/chrono-operators.md#operator-)|Operador para la resta o la negación de objetos `duration` y `time_point`.|
|[operator!=](../standard-library/chrono-operators.md#op_neq)|Operador de desigualdad que se utiliza con objetos `duration` o `time_point`.|
|[operator modulo](../standard-library/chrono-operators.md#op_modulo)|Operador para operaciones de módulo en objetos `duration`.|
|[operator*](../standard-library/chrono-operators.md#op_star)|Operador de multiplicación para objetos `duration`.|
|[operator/](../standard-library/chrono-operators.md#op_div)|Operador de división para objetos `duration`.|
|[operator+](../standard-library/chrono-operators.md#op_add)|Agrega objetos `duration` y `time_point`.|
|[operator&lt;](../standard-library/chrono-operators.md#op_lt)|Determina si un objeto `duration` o `time_point` es menor que otro objeto `duration` o `time_point`.|
|[operator&lt;=](../standard-library/chrono-operators.md#op_lt_eq)|Determina si un objeto `duration` o `time_point` es menor o igual que otro objeto `duration` o `time_point`.|
|[operator==](../standard-library/chrono-operators.md#op_eq_eq)|Determina si dos objetos `duration` representan intervalos de tiempo de la misma longitud o si dos objetos `time_point` representan el mismo punto en el tiempo.|
|[operator&gt;](../standard-library/chrono-operators.md#op_gt)|Determina si un objeto `duration` o `time_point` es mayor que otro objeto `duration` o `time_point`.|
|[operator&gt;=](../standard-library/chrono-operators.md#op_gt_eq)|Determina si un objeto `duration` o `time_point` es mayor o igual que otro objeto `duration` o `time_point`.|

### <a name="typedefs-predefined-duration-types"></a>Typedefs (tipos de duración predefinidos)

Para obtener más información sobre los tipos de relación que se usan en los siguientes typedefs, vea [\<ratio>](../standard-library/ratio.md).

|||
|-|-|
|`typedef duration<long long, nano> nanoseconds;`|Sinónimo de un tipo de `duration` que tiene un período de paso de 1 nanosegundo.|
|`typedef duration<long long, micro> microseconds;`|Sinónimo de un tipo de `duration` que tiene un período de paso de 1 microsegundo.|
|`typedef duration<long long, milli> milliseconds;`|Sinónimo de un tipo de `duration` que tiene un período de paso de 1 milisegundo.|
|`typedef duration<long long> seconds;`|Sinónimo de un tipo de `duration` que tiene un período de paso de 1 segundo.|
|`typedef duration<int, ratio<60> > minutes;`|Sinónimo de un tipo de `duration` que tiene un período de paso de 1 minuto.|
|`typedef duration<int, ratio<3600> > hours;`|Sinónimo de un tipo de `duration` que tiene un período de paso de 1 hora.|

### <a name="literals"></a>Literales

**(C++ 11)** El encabezado \<chrono > define los siguientes [literales definidos](../cpp/user-defined-literals-cpp.md) por el usuario que puede usar para mayor comodidad, seguridad de tipos y mantenimiento del código. Estos literales se definen en el espacio de nombres alineado `literals::chrono_literals` y están en ámbito cuando std:: chrono está en ámbito.

|||
|-|-|
|operador de horas "" h (unsigned Long Long Val)|Especifica horas como un valor entero.|
|duración \<double, ratio \<3600 > > operador "" h (Long Double Val)|Especifica horas como un valor de coma flotante.|
|minutos (operador "" min) (unsigned Long Long Val)|Especifica minutos como un valor entero.|
|duración \<double, ratio \<60 > > (operador "" min) (Long Double Val)|Especifica minutos como un valor de coma flotante.|
|seconds Operator "" s (unsigned Long Long Val)|Especifica minutos como un valor entero.|
|Duration \<double > operador "" s (Long Double Val)|Especifica segundos como un valor de coma flotante.|
|operador de milisegundos "" MS (unsigned Long Long Val)|Especifica milisegundos como un valor entero.|
|Duration \<double, milisegundo > operador "" MS (Long Double Val)|Especifica milisegundos como un valor de coma flotante.|
|operador de microsegundos "" US (unsigned Long Long Val)|Especifica microsegundos como un valor entero.|
|Duration \<double, micro > operador "" US (Long Double Val)|Especifica microsegundos como un valor de coma flotante.|
|operador de nanosegundos "" NS (unsigned Long Long Val)|Especifica nanosegundos como un valor entero.|
|Duration \<double, nano > operador "" NS (Long Double Val)|Especifica nanosegundos como un valor de coma flotante.|

En los siguientes ejemplos, se muestra cómo usar los literales chrono.

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)
