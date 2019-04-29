---
title: Error del compilador C3744
ms.date: 11/04/2016
f1_keywords:
- C3744
helpviewer_keywords:
- C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
ms.openlocfilehash: 407ed4b30b55b63aa9bf36de9f8675a531d70534
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62227116"
---
# <a name="compiler-error-c3744"></a>Error del compilador C3744

__unhook debe tener al menos 3 argumentos para eventos administrados

El [__unhook](../../cpp/unhook.md) función debe tomar tres parámetros cuando se utiliza en un programa que se compila con extensiones administradas para C++.

`__hook` y `__unhook` no son compatibles con la programación/CLR. Utilice los operadores += y -=.

Solo es accesible a través de la opción del compilador obsoleto C3744 **/CLR: oldSyntax**.
