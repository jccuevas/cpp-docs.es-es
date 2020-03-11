---
title: Definiciones de tipo de &lt;type_traits&gt;
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::false_type
- xtr1common/std::false_type
- type_traits/std::true_type
- xtr1common/std::true_type
ms.assetid: 8ac040ca-ed2d-4570-adc9-cb5626530053
ms.openlocfilehash: eff1a99fb95f15c6377e8a74cca36e718cbd6fd9
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78867223"
---
# <a name="lttype_traitsgt-typedefs"></a>Definiciones de tipo de &lt;type_traits&gt;

|||
|-|-|
|[false_type](#false_type)|[true_type](#true_type)|

## <a name="false_type"></a>  false_type (Definición de tipo)

Contiene la constante integral con valor false.

```cpp
typedef integral_constant<bool, false> false_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de una especialización de la plantilla `integral_constant`.

### <a name="example"></a>Ejemplo

```cpp
#include <type_traits>
#include <iostream>

int main() {
    std::cout << "false_type == " << std::boolalpha
        << std::false_type::value << std::endl;
    std::cout << "true_type == " << std::boolalpha
        << std::true_type::value << std::endl;

    return (0);
}
```

```Output
false_type == false
true_type == true
```

## <a name="true_type"></a>  true_type (Definición de tipo)

Contiene la constante integral con valor true.

```cpp
typedef integral_constant<bool, true> true_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de una especialización de la plantilla `integral_constant`.

### <a name="example"></a>Ejemplo

```cpp
// std__type_traits__true_type.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main() {
    std::cout << "false_type == " << std::boolalpha
        << std::false_type::value << std::endl;
    std::cout << "true_type == " << std::boolalpha
        << std::true_type::value << std::endl;

    return (0);
}
```

```Output
false_type == false
true_type == true
```

## <a name="see-also"></a>Consulte también

[<type_traits>](../standard-library/type-traits.md)
