---
title: Error del compilador C2692
ms.date: 11/04/2016
f1_keywords:
- C2692
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
ms.openlocfilehash: c469f4944417c9116c7316b01642dd4b370b8c4b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257821"
---
# <a name="compiler-error-c2692"></a>Error del compilador C2692

'nombre_de_función': ajusten completamente al prototipo funciones requeridas en el compilador de C con el ' / clr' opción

Cuando se compila para .NET de código administrado, el compilador de C requiere que las declaraciones de función de ANSI. Además, si una función no toma parámetros, debe declarar explícitamente `void` como el tipo de parámetro.