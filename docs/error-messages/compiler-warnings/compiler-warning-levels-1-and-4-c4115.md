---
title: Advertencia del compilador (niveles 1 y 4) C4115
ms.date: 11/04/2016
f1_keywords:
- C4115
helpviewer_keywords:
- C4115
ms.assetid: f3f94e72-fc49-4d09-b3e7-23d68e61152f
ms.openlocfilehash: 7e39e8c837d94776a804da2bf38643b453edb949
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198047"
---
# <a name="compiler-warning-levels-1-and-4-c4115"></a>Advertencia del compilador (niveles 1 y 4) C4115

'type': definición de tipo con nombre entre paréntesis

Un símbolo determinado se usa para definir una estructura, una unión o un tipo enumerado dentro de una expresión entre paréntesis. El ámbito de la definición de puede ser inesperado.

En una llamada de función de C, la definición tiene ámbito global. En una llamada de C++, la definición tiene el mismo ámbito que la función que se llama.

Esta advertencia puede deberse también a declaradores entre paréntesis (como los prototipos) que no son expresiones entre paréntesis.

Se trata de una advertencia de nivel 1 con programas de C++ y programas de C que se compilaron con la compatibilidad con ANSI (/Za). De lo contrario, es de nivel 3.
