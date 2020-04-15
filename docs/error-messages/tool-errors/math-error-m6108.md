---
title: Error matemático M6108
ms.date: 11/04/2016
f1_keywords:
- M6108
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
ms.openlocfilehash: c6bd403437ee5e55eaf4add288995d0e4aa76c3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361973"
---
# <a name="math-error-m6108"></a>Error matemático M6108

raíz cuadrada

El operando en una operación de raíz cuadrada era negativo.

El programa finaliza con el código de salida 136.

> [!NOTE]
> La `sqrt` función de la biblioteca en tiempo de ejecución de C y la función intrínseca **FORTRAN SQRT** no generan este error. La `sqrt` función C comprueba el argumento antes de realizar la operación y devuelve un valor de error si el operando es negativo. La función FORTRAN **SQRT** genera el error DOMAIN [M6201](../../error-messages/tool-errors/math-error-m6201.md) en lugar de este error.
