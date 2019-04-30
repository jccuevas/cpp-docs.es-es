---
title: Error matemático M6108
ms.date: 11/04/2016
f1_keywords:
- M6108
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
ms.openlocfilehash: d60e9b6284c79828fda1f7af542fcf197f189ad0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393277"
---
# <a name="math-error-m6108"></a>Error matemático M6108

raíz cuadrada

El operando de una operación de raíz cuadrada era negativo.

El programa termina con el código de salida 136.

> [!NOTE]
>  El `sqrt` función en la biblioteca de tiempo de ejecución de C y la función intrínseca FORTRAN **SQRT** no generan este error. La C `sqrt` función comprueba el argumento antes de realizar la operación y devuelve un valor de error si el operando es negativo. El FORTRAN **SQRT** función genera el error de dominio [M6201](../../error-messages/tool-errors/math-error-m6201.md) en lugar de este error.