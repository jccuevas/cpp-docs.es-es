---
title: Constantes de caracteres de C
ms.date: 11/04/2016
helpviewer_keywords:
- characters, constants
- (') single quotation mark
- constants, character
- single quotation mark
ms.assetid: 388ae7d7-2c3a-44d6-a507-63f541ecd2da
ms.openlocfilehash: 5d87b57726f741cc96f2180de33cae01403786ec
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152773"
---
# <a name="c-character-constants"></a>Constantes de caracteres de C

Una "constante de carácter" se forma agregando un carácter individual del juego de caracteres que se puede representar dentro de comillas simples (**' '**). Las constantes de caracteres se utilizan para representar los caracteres del [juego de caracteres de la ejecución](../c-language/execution-character-set.md).

## <a name="syntax"></a>Sintaxis

*character-constant*: **'** *c-char-sequence* **'**

**L'** *c-char-sequence* **'**

*c-char-sequence*: *c-char*

*c-char-sequence c-char*

*c-char*: Cualquier miembro del juego de caracteres de origen, excepto la comilla simple (**'**), la barra diagonal inversa (**\\**) o el carácter de nueva línea

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
