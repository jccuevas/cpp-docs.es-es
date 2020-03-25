---
title: Error matemático M6201
ms.date: 11/04/2016
f1_keywords:
- M6201
helpviewer_keywords:
- M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
ms.openlocfilehash: 0b1cd0d3fcd86a2174b19da41176dd97f547a295
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193711"
---
# <a name="math-error-m6201"></a>Error matemático M6201

' función ': error de _DOMAIN

Un argumento de la función especificada estaba fuera del dominio de valores de entrada válidos para esa función.

## <a name="example"></a>Ejemplo

```
result = sqrt(-1.0)   // C statement
result = SQRT(-1.0)   !  FORTRAN statement
```

Este error llama a la función `_matherr` con el nombre de la función, sus argumentos y el tipo de error. Puede volver a escribir la función `_matherr` para personalizar el control de determinados errores matemáticos de punto flotante en tiempo de ejecución.
