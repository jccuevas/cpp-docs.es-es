---
title: Error matemático M6108
ms.date: 11/04/2016
f1_keywords:
- M6108
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
ms.openlocfilehash: 68e6ae823613d87eb01c443b564b46746259cd7b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173730"
---
# <a name="math-error-m6108"></a>Error matemático M6108

raíz cuadrada

El operando de una operación de raíz cuadrada era negativo.

El programa finaliza con el código de salida 136.

> [!NOTE]
>  La función `sqrt` de la biblioteca en tiempo de ejecución de C y la función intrínseca de FORTRAN **sqrt** no genera este error. La función `sqrt` de C comprueba el argumento antes de realizar la operación y devuelve un valor de error si el operando es negativo. La función **sqrt** de Fortran genera el error de dominio [matemático m6201](../../error-messages/tool-errors/math-error-m6201.md) en lugar de este error.
