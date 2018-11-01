---
title: Estructura hash (biblioteca estándar de C++) | Microsoft Docs
ms.date: 11/04/2016
f1_keywords:
- thread/std::hash
ms.assetid: 4a8bf5bc-4334-4070-936b-98585f8a073b
ms.openlocfilehash: bb230d401d5061f4951f8007f93c3a28ce3dab03
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579876"
---
# <a name="hash-structure-c-standard-library"></a>Estructura hash (biblioteca estándar de C++)

Define una función miembro que devuelve un valor que se determina de forma exclusiva mediante `Val`. La función miembro define una función [hash](../standard-library/hash-class.md) adecuada para asignar valores de tipo `thread::id` a una distribución de valores de índice.

## <a name="syntax"></a>Sintaxis

```cpp
template <>
struct hash<thread::id> :
    public unary_function<thread::id, size_t>
{
    size_t operator()(thread::id Val) const;

};
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<subproceso >

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<thread>](../standard-library/thread.md)<br/>
[unary_function (Struct)](../standard-library/unary-function-struct.md)<br/>
