---
title: money_base (Clase)
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::money_base
helpviewer_keywords:
- money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
ms.openlocfilehash: 5b19635cf4d2cce58ec50226c463a075cfac5b0f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455562"
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

La enumeración `part` describe los valores posibles de los elementos del campo de matriz en el patrón de estructura. Los valores de `part` son:

- `none`para buscar coincidencias con cero o más espacios o no generar nada.

- `sign`para buscar o generar un signo positivo o negativo.

- `space`para buscar coincidencias con cero o más espacios o generar un espacio.

- `symbol`para hacer coincidir o generar un símbolo de moneda.

- `value`para hacer coincidir o generar un valor monetario.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
