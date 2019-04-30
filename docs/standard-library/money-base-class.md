---
title: money_base (Clase)
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::money_base
helpviewer_keywords:
- money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
ms.openlocfilehash: b0c77b523dbe31bc5b07ae3d736441880fe04546
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383573"
---
# <a name="moneybase-class"></a>money_base (Clase)

La clase describe una enumeración y una estructura común a todas las especializaciones de la clase de plantilla [moneypunct](../standard-library/moneypunct-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
struct pattern
{
   char field[_PATTERN_FIELD_SIZE];
};
```

## <a name="remarks"></a>Comentarios

La enumeración `part` describe los posibles valores de los elementos del campo de matriz en el patrón de estructura. Los valores de `part` son:

- `none` Para hacer coincidir cero o más espacios o generar nada.

- `sign` para buscar o generar un signo positivo o negativo.

- `space` Para hacer coincidir cero o más espacios o generar un espacio.

- `symbol` para buscar o generar un símbolo de moneda.

- `value` para buscar o generar un valor monetario.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
