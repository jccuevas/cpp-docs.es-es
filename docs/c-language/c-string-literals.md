---
title: Literales de cadena de C | Microsoft Docs
ms.custom: ''
ms.date: 08/31/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- string literals, syntax
- strings [C++], string literals
- literal strings, C
ms.assetid: 4b05523e-49a2-4900-b21a-754350af3328
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 57bd79e1df35f650d78da3108137d58405b33f25
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082019"
---
# <a name="c-string-literals"></a>Literales de cadena de C

Un "literal de cadena" es una secuencia de caracteres del juego de caracteres de origen incluida entre comillas dobles (**" "**). Los literales de cadena se utilizan para representar una secuencia de caracteres que, en conjunto, forman una cadena terminada en null. Siempre debe agregar como prefijo la letra **L** a los literales de cadena anchos.

## <a name="syntax"></a>Sintaxis

*string-literal*: &nbsp;&nbsp;&nbsp;&nbsp;**"** *s-char-sequence*<sub>opt</sub> **"** &nbsp;&nbsp;&nbsp;&nbsp;**L"** *s-char-sequence*<sub>opt</sub> **"**

*s-char-sequence*: &nbsp;&nbsp;&nbsp;&nbsp;*s-char* &nbsp;&nbsp;&nbsp;&nbsp;*s-char-sequence* *s-char*

*s-char*: &nbsp;&nbsp;&nbsp;&nbsp;cualquier miembro del juego de caracteres de origen excepto las comillas dobles ("), la barra diagonal inversa (\\) o el carácter de nueva línea &nbsp;&nbsp;&nbsp;&nbsp;*escape-sequence*

## <a name="remarks"></a>Comentarios

El ejemplo siguiente es un literal de cadena simple:

```C
char *amessage = "This is a string literal.";
```

Todos los códigos de escape mostrados en la tabla [Secuencias de escape](../c-language/escape-sequences.md) son válidos en literales de cadena. Para representar un carácter de comillas dobles en un literal de cadena, utilice la secuencia de escape **\\"**. El carácter de comilla simple (**'**) se puede representar sin una secuencia de escape. La barra diagonal inversa (**\\**) deben ir seguida de una segunda barra diagonal inversa (**\\\\**) cuando aparece dentro de una cadena. Cuando una barra diagonal inversa aparece al final de una línea, se interpreta siempre como un carácter de continuación de línea.

## <a name="see-also"></a>Vea también

[Elementos de C](../c-language/elements-of-c.md)
