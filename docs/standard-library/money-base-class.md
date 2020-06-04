---
title: money_base (Clase)
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::money_base
helpviewer_keywords:
- money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
ms.openlocfilehash: c614832b0cbb1cc23e42ecb3a939ccf1334a5cea
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689321"
---
# <a name="money_base-class"></a>money_base (Clase)

La clase describe una enumeración y una estructura común a todas las especializaciones de la plantilla de clase [moneypunct](../standard-library/moneypunct-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
struct pattern
{
   char field[_PATTERN_FIELD_SIZE];
};
```

## <a name="remarks"></a>Comentarios

La enumeración `part` describe los valores posibles de los elementos del campo de matriz en el patrón de estructura. Los valores de `part` son:

- `none` para buscar coincidencias con cero o más espacios o no generar nada.

- `sign` para hacer coincidir o generar un signo positivo o negativo.

- `space` para buscar coincidencias con cero o más espacios o generar un espacio.

- `symbol` para buscar o generar un símbolo de divisa.

- `value` para hacer coincidir o generar un valor monetario.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
