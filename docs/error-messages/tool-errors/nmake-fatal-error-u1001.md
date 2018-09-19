---
title: Error grave de NMAKE U1001 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1001
dev_langs:
- C++
helpviewer_keywords:
- U1001
ms.assetid: 5d7da559-6cbd-44d6-848c-aaf54cae0d1a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4e465af5b4fa22c5f0ba5a9e01ebde0a7ee89e9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068148"
---
# <a name="nmake-fatal-error-u1001"></a>Error grave de NMAKE U1001

error de sintaxis: carácter no válido 'character' en macro

El carácter especificado aparece en una macro, pero no es una letra, número o carácter de subrayado.

Este error puede deberse a que faltan dos puntos en una expansión de macro:

```
syntax error : illegal character '=' in macro
```