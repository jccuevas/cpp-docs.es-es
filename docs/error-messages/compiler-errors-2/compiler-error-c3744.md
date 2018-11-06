---
title: Error del compilador C3744
ms.date: 11/04/2016
f1_keywords:
- C3744
helpviewer_keywords:
- C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
ms.openlocfilehash: 407ed4b30b55b63aa9bf36de9f8675a531d70534
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516238"
---
# <a name="compiler-error-c3744"></a>Error del compilador C3744

__unhook debe tener al menos 3 argumentos para eventos administrados

El [__unhook](../../cpp/unhook.md) función debe tomar tres parámetros cuando se utiliza en un programa que se compila con extensiones administradas para C++.

`__hook` y `__unhook` no son compatibles con la programación/CLR. Utilice los operadores += y -=.

Solo es accesible a través de la opción del compilador obsoleto C3744 **/CLR: oldSyntax**.
