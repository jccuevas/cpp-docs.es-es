---
title: Error del compilador C2692
ms.date: 11/04/2016
f1_keywords:
- C2692
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
ms.openlocfilehash: c469f4944417c9116c7316b01642dd4b370b8c4b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611164"
---
# <a name="compiler-error-c2692"></a>Error del compilador C2692

'nombre_de_función': ajusten completamente al prototipo funciones requeridas en el compilador de C con el ' / clr' opción

Cuando se compila para .NET de código administrado, el compilador de C requiere que las declaraciones de función de ANSI. Además, si una función no toma parámetros, debe declarar explícitamente `void` como el tipo de parámetro.