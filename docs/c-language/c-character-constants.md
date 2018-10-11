---
title: Constantes de caracteres de C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- characters, constants
- (') single quotation mark
- constants, character
- single quotation mark
ms.assetid: 388ae7d7-2c3a-44d6-a507-63f541ecd2da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f9908bfd8be662a53727e9c833626f329dd45c04
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038586"
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