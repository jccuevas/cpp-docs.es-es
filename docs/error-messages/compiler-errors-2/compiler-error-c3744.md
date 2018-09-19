---
title: Error del compilador C3744 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3744
dev_langs:
- C++
helpviewer_keywords:
- C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d644a621fc6d8e460e1b97e5baec360de8662365
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063728"
---
# <a name="compiler-error-c3744"></a>Error del compilador C3744

__unhook debe tener al menos 3 argumentos para eventos administrados

El [__unhook](../../cpp/unhook.md) función debe tomar tres parámetros cuando se utiliza en un programa que se compila con extensiones administradas para C++.

`__hook` y `__unhook` no son compatibles con la programación/CLR. Utilice los operadores += y -=.

Solo es accesible a través de la opción del compilador obsoleto C3744 **/CLR: oldSyntax**.
