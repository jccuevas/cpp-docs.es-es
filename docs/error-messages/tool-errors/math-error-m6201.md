---
title: Error matemático M6201
ms.date: 11/04/2016
f1_keywords:
- M6201
helpviewer_keywords:
- M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
ms.openlocfilehash: 6d3f107de7e45653374036ecafaa864cb3eff5b0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393251"
---
# <a name="math-error-m6201"></a>Error matemático M6201

'function': error de _dominio

Un argumento a la función especificada no era fuera del dominio de los valores de entrada válidos para esa función.

## <a name="example"></a>Ejemplo

```
result = sqrt(-1.0)   // C statement
result = SQRT(-1.0)   !  FORTRAN statement
```

Este error invoca el `_matherr` función con el nombre de función, sus argumentos y el tipo de error. Puede volver a escribir el `_matherr` función para personalizar el tratamiento de determinados errores de tiempo de ejecución matemático de punto flotante.