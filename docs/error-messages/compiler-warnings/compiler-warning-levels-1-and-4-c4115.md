---
title: Compilador advertencia (niveles 1 y 4) C4115 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4115
dev_langs:
- C++
helpviewer_keywords:
- C4115
ms.assetid: f3f94e72-fc49-4d09-b3e7-23d68e61152f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6c22e3c33f9ef2409c02f0e651473d566b4d2a74
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022531"
---
# <a name="compiler-warning-levels-1-and-4-c4115"></a>Advertencia del compilador (niveles 1 y 4) C4115

'type': definición de tipo con nombre entre paréntesis

Un símbolo determinado se usa para definir una estructura, una unión o un tipo enumerado dentro de una expresión entre paréntesis. El ámbito de la definición de puede ser inesperado.

En una llamada de función de C, la definición tiene ámbito global. En una llamada de C++, la definición tiene el mismo ámbito que la función que se llama.

Esta advertencia puede deberse también a declaradores entre paréntesis (como los prototipos) que no son expresiones entre paréntesis.

Se trata de una advertencia de nivel 1 con programas de C++ y programas de C que se compilaron con la compatibilidad con ANSI (/Za). De lo contrario, es de nivel 3.