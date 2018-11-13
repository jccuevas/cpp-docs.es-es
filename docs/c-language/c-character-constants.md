---
title: Constantes de caracteres de C
ms.date: 11/04/2016
helpviewer_keywords:
- characters, constants
- (') single quotation mark
- constants, character
- single quotation mark
ms.assetid: 388ae7d7-2c3a-44d6-a507-63f541ecd2da
ms.openlocfilehash: 684763b5ce3983b6efc44db9499c139c84f6e3aa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507199"
---
# <a name="c-character-constants"></a>Constantes de caracteres de C

Una "constante de carácter" se forma agregando un carácter individual del juego de caracteres que se puede representar dentro de comillas simples (**' '**). Las constantes de caracteres se utilizan para representar los caracteres del [juego de caracteres de la ejecución](../c-language/execution-character-set.md).

## <a name="syntax"></a>Sintaxis

*character-constant*: **'** *c-char-sequence* **'**

**L'** *c-char-sequence* **'**

*c-char-sequence*: *c-char*

*c-char-sequence c-char*

*c-char*: cualquier miembro del juego de caracteres de origen, excepto la comilla simple (**'**), la barra diagonal inversa (**\\**) o el carácter de nueva línea

*escape-sequence*

*escape-sequence*: *simple-escape-sequence*

*octal-escape-sequence*

*hexadecimal-escape-sequence*

*simple-escape-sequence*: uno de **\a \b \f \n \r \t \v**

**\\' \\" \\\ \\?**

*octal-escape-sequence*: **\\**  *octal-digit*

**\\**  *octal-digit octal-digit*

**\\**  *octal-digit octal-digit octal-digit*

*hexadecimal-escape-sequence*: **\x**  *hexadecimal-digit*

*hexadecimal-escape-sequence hexadecimal-digit*

## <a name="see-also"></a>Vea también

[Constantes de C](../c-language/c-constants.md)