---
title: Intervalo de valores char
ms.date: 11/04/2016
ms.assetid: 15ae9781-ec21-4333-bba8-6d2383bbf7f1
ms.openlocfilehash: 8cb2609aca910056b5243fddc868710581e576e7
ms.sourcegitcommit: 9266fc76ac2e872e35a208b4249660dfdfc87cba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2020
ms.locfileid: "81480902"
---
# <a name="range-of-char-values"></a>Intervalo de valores char

**ANSI 3.2.1.1** Si un **char** "simple" tiene el mismo rango de valores que un **char firmado** o un **char sin signo**

Todos los valores de caracteres con signo van de -128 a 127. Todos los valores de caracteres sin signo van 0 a 255.

La [`/J`](../build/reference/j-default-char-type-is-unsigned.md) opción del compilador cambia el tipo predeterminado para **char** de **signed char** a **unsigned char**.

## <a name="see-also"></a>Consulte también

[Characters](../c-language/characters.md)
