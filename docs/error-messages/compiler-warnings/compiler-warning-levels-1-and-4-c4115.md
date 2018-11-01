---
title: Advertencia del compilador (niveles 1 y 4) C4115
ms.date: 11/04/2016
f1_keywords:
- C4115
helpviewer_keywords:
- C4115
ms.assetid: f3f94e72-fc49-4d09-b3e7-23d68e61152f
ms.openlocfilehash: 20e44eba3b6f6079e6f37b7cf33fa530a996e829
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462964"
---
# <a name="compiler-warning-levels-1-and-4-c4115"></a>Advertencia del compilador (niveles 1 y 4) C4115

'type': definición de tipo con nombre entre paréntesis

Un símbolo determinado se usa para definir una estructura, una unión o un tipo enumerado dentro de una expresión entre paréntesis. El ámbito de la definición de puede ser inesperado.

En una llamada de función de C, la definición tiene ámbito global. En una llamada de C++, la definición tiene el mismo ámbito que la función que se llama.

Esta advertencia puede deberse también a declaradores entre paréntesis (como los prototipos) que no son expresiones entre paréntesis.

Se trata de una advertencia de nivel 1 con programas de C++ y programas de C que se compilaron con la compatibilidad con ANSI (/Za). De lo contrario, es de nivel 3.