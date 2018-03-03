---
title: Literales de cadena de C | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- string literals, syntax
- strings [C++], string literals
- literal strings, C
ms.assetid: 4b05523e-49a2-4900-b21a-754350af3328
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b0be3ee70ef708441d20fdbbc14f25f5102d734a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="c-string-literals"></a>Literales de cadena de C
Un "literal de cadena" es una secuencia de caracteres del juego de caracteres de origen incluida entre comillas dobles (**" "**). Los literales de cadena se utilizan para representar una secuencia de caracteres que, en conjunto, forman una cadena terminada en null. Siempre debe agregar como prefijo la letra **L** a los literales de cadena anchos.  
  
## <a name="syntax"></a>Sintaxis  
 *string-literal*:  
 **"** *s-char-sequence* opt**"**  
  
 **L"** *s-char-sequence* opt**"**  
  
 *s-char-sequence*:  
 *s-char*  
  
 *s-char-sequence s-char*  
  
 *s-char*:  
 cualquier miembro del juego de caracteres de origen excepto las comillas dobles ("), la barra diagonal inversa (\\) o el carácter de nueva línea  
  
 *escape-sequence*  
  
 El ejemplo siguiente es un literal de cadena simple:  
  
```  
char *amessage = "This is a string literal.";  
```  
  
 Todos los códigos de escape mostrados en la tabla [Secuencias de escape](../c-language/escape-sequences.md) son válidos en literales de cadena. Para representar un carácter de comillas dobles en un literal de cadena, utilice la secuencia de escape **\\"**. El carácter de comilla simple (**'**) se puede representar sin una secuencia de escape. La barra diagonal inversa (**\\**) deben ir seguida de una segunda barra diagonal inversa (**\\\\**) cuando aparece dentro de una cadena. Cuando una barra diagonal inversa aparece al final de una línea, se interpreta siempre como un carácter de continuación de línea.  
  
## <a name="see-also"></a>Vea también  
 [Elementos de C](../c-language/elements-of-c.md)