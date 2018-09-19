---
title: Error matemático M6108 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6108
dev_langs:
- C++
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1624a89b472733b4adb5563c8ba52e0b03dcaa2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048622"
---
# <a name="math-error-m6108"></a>Error matemático M6108

raíz cuadrada

El operando de una operación de raíz cuadrada era negativo.

El programa termina con el código de salida 136.

> [!NOTE]
>  El `sqrt` función en la biblioteca de tiempo de ejecución de C y la función intrínseca FORTRAN **SQRT** no generan este error. La C `sqrt` función comprueba el argumento antes de realizar la operación y devuelve un valor de error si el operando es negativo. El FORTRAN **SQRT** función genera el error de dominio [M6201](../../error-messages/tool-errors/math-error-m6201.md) en lugar de este error.