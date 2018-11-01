---
title: Error grave de NMAKE U1001
ms.date: 11/04/2016
f1_keywords:
- U1001
helpviewer_keywords:
- U1001
ms.assetid: 5d7da559-6cbd-44d6-848c-aaf54cae0d1a
ms.openlocfilehash: bfe2edf9c57eda073826a8c161ae0c358f3a6232
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662246"
---
# <a name="nmake-fatal-error-u1001"></a>Error grave de NMAKE U1001

error de sintaxis: carácter no válido 'character' en macro

El carácter especificado aparece en una macro, pero no es una letra, número o carácter de subrayado.

Este error puede deberse a que faltan dos puntos en una expansión de macro:

```
syntax error : illegal character '=' in macro
```