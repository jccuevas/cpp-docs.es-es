---
title: Constantes de caracteres de C | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- characters, constants
- (') single quotation mark
- constants, character
- single quotation mark
ms.assetid: 388ae7d7-2c3a-44d6-a507-63f541ecd2da
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 374870a385e12d301731c0f9232d09895d8906c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="c-character-constants"></a>Constantes de caracteres de C
Una "constante de carácter" se forma agregando un carácter individual del juego de caracteres que se puede representar dentro de comillas simples (**' '**). Las constantes de caracteres se utilizan para representar los caracteres del [juego de caracteres de la ejecución](../c-language/execution-character-set.md).  
  
## <a name="syntax"></a>Sintaxis  
 *character-constant*:  
 **'** *c-char-sequence* **'**  
  
 **L'** *c-char-sequence* **'**  
  
 *c-char-sequence*:  
 *c-char*  
  
 *c-char-sequence c-char*  
  
 *c-char*:  
 Cualquier miembro del juego de caracteres de origen, excepto la comilla simple (**'**), la barra diagonal inversa (**\\**) o el carácter de nueva línea  
  
 *escape-sequence*  
  
 *escape-sequence*:  
 *simple-escape-sequence*  
  
 *octal-escape-sequence*  
  
 *hexadecimal-escape-sequence*  
  
 *simple-escape-sequence*: uno de  
 **\a \b \f \n \r \t \v**  
  
 **\\' \\" \\\ \\?**  
  
 *octal-escape-sequence*:  
 **\\**  *octal-digit*  
  
 **\\**  *octal-digit octal-digit*  
  
 **\\**  *octal-digit octal-digit octal-digit*  
  
 *hexadecimal-escape-sequence*:  
 **\x**  *hexadecimal-digit*  
  
 *hexadecimal-escape-sequence hexadecimal-digit*  
  
## <a name="see-also"></a>Vea también  
 [Constantes de C](../c-language/c-constants.md)