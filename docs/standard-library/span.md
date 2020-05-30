---
title: '&lt;extienda&gt;'
ms.date: 05/28/2020
f1_keywords:
- <span>
helpviewer_keywords:
- span header
ms.openlocfilehash: ebd0a30c677ea44f95e64e2d2ba010bc99cb412b
ms.sourcegitcommit: 1a8fac06478da8bee1f6d70e25afbad94144af1a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/30/2020
ms.locfileid: "84226317"
---
# <a name="ltspangt"></a>&lt;extienda&gt;

Una `span` es una vista de una secuencia contigua de objetos. Proporciona un acceso rápido y seguro para límites. A diferencia de `vector` o `array` , no "posee" los elementos a los que proporciona acceso. 

Consulte [span (clase](span-class.md) ) para obtener información detallada. A continuación se muestra un ejemplo de cómo se puede usar un intervalo:

```cpp
#include <span>
#include <iostream>

void Show(std::span<int> someValues)
{
    // show values in reverse
    for (auto rIt = someValues.rbegin(); rIt != someValues.rend(); ++rIt)
    {
        std::cout << *rIt;
    }

    // show a subspan
    for (auto& i : someValues.subspan(1, 2))
    {
        std::cout << i;
    }
}

int main()
{
    int numbers[]{ 0,1,2,3,4 };
    Show(numbers); // note conversion from array to span
}
```

## <a name="requirements"></a>Requisitos

**Encabezado:**\<span>

**Espacio de nombres:** std

**Opción del compilador:** /STD: c + + latest

## <a name="members"></a>Miembros

### <a name="classes"></a>Clases

|||
|-|:-|
|[extienda](span-class.md)| Proporciona una vista sobre una secuencia contigua de objetos. |

### <a name="operators"></a>Operadores

|||
|-|:-|
|[operador =](span-class.md#op_eq)| Asignación de intervalo |
|[Operator\[\]](span-class.md#op_at)| Acceso a elementos |

### <a name="functions"></a>Functions

|||
|-|:-|
| [as_bytes](span-functions.md#as_bytes)| Obtiene los bytes de solo lectura subyacentes del intervalo. |
| [as_writable_bytes](span-functions.md#as_writable_bytes) | Obtiene los bytes subyacentes del intervalo. |

### <a name="constants"></a>Constantes

|||
|-|:-|
| **dynamic_extent** | Indica que el tamaño del intervalo se determina en tiempo de ejecución en lugar de en tiempo de compilación. Cuando se conoce el número de elementos del intervalo en tiempo de compilación, se especifica como el `Extent` parámetro de plantilla. Si no se conoce el número hasta el tiempo de ejecución, especifique `dynamic_extent` en su lugar. |

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)
