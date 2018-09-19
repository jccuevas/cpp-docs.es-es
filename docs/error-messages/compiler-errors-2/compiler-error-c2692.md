---
title: Error del compilador C2692 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2692
dev_langs:
- C++
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 03a9006889c5853e77b5603484ea9d18f2474241
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088376"
---
# <a name="compiler-error-c2692"></a>Error del compilador C2692

'nombre_de_función': ajusten completamente al prototipo funciones requeridas en el compilador de C con el ' / clr' opción

Cuando se compila para .NET de código administrado, el compilador de C requiere que las declaraciones de función de ANSI. Además, si una función no toma parámetros, debe declarar explícitamente `void` como el tipo de parámetro.