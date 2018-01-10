---
title: Secuencias de escape | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- "\r escape sequence"
- double backslash
- horizontal-tab 	 escape sequence
- (') single quotation mark
- "bell character \a escape sequence"
- escape sequences
- hexadecimal escape sequence
- carriage returns
- tab 	 escape sequence
- "\f escape sequence"
- quotation marks, single
- "formfeed \f escape sequence"
- "\v escape sequence"
- control character escape sequences
- " symbol in escape sequences"
- octal escape sequence
- escape characters
- "newline character \n escape sequence"
- nongraphic control characters
- question mark, literal
- "\nescape sequence"
- "vertical tab \v escape sequence"
- "\a escape sequence"
- '? symbol'
- '? symbol, escape sequence character'
- "	 escape sequence"
- backspace escape sequence
ms.assetid: 5aef377f-a76c-4d5c-aa04-8308758ad6a8
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d341aa5af2b16d1a29bc4e3dfe2f97a68b73d6ba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="escape-sequences"></a>Secuencias de escape
Las combinaciones de caracteres que consisten en una barra diagonal inversa (**\\**) seguida de una letra o una combinación de dígitos se denominan "secuencias de escape". Para representar un carácter de nueva línea, una comilla simple u otros caracteres de una constante de caracteres, debe utilizar secuencias de escape. Una secuencia de escape se considera un carácter individual y por tanto es válida como constante de caracteres.  
  
 Las secuencias de escape se suelen utilizar para especificar acciones como retornos de carro y movimientos de tabulación en terminales e impresoras. También se emplean para proporcionar representaciones literales de caracteres no imprimibles y de caracteres que normalmente tienen significados especiales, como las comillas dobles (**"**). En la tabla siguiente se enumeran las secuencias de escape ANSI y lo que representan.  
  
 Tenga en cuenta que el signo de interrogación precedido de una barra diagonal inversa (**\\?**) especifica un signo de interrogación literal en aquellos casos en los que la secuencia de caracteres se malinterpretaría como un trígrafo. Vea [Trígrafos](../c-language/trigraphs.md) para obtener más información.  
  
### <a name="escape-sequences"></a>Secuencias de escape  
  
|Secuencia de escape|Representa|  
|---------------------|----------------|  
|**\a**|Campana (alerta)|  
|**\b**|Retroceso|  
|**\f**|Avance de página|  
|**\n**|Nueva línea|  
|**\r**|Retorno de carro|  
|**\t**|Tabulación horizontal|  
|**\v**|Tabulación vertical|  
|**\\'**|Comilla simple|  
|**\\"**|Comillas dobles|  
|**\\\\**|Barra diagonal inversa|  
|**\\?**|Signo de interrogación literal|  
|**\\** *ooo*|Carácter ASCII en notación octal|  
|**\x** *hh*|Carácter ASCII en notación hexadecimal|  
|**\x** *hhhh*|Carácter Unicode en notación hexadecimal si esta secuencia de escape se utiliza en una constante de caracteres anchos o un literal de cadena Unicode.<br /><br /> Por ejemplo: `WCHAR f = L'\x4e00'` o `WCHAR b[] = L"The Chinese character for one is \x4e00"`.|  
  
 **Específicos de Microsoft**  
  
 Si una barra diagonal inversa precede a un carácter que no aparece en la tabla, el compilador controla el carácter no definido como el propio carácter. Por ejemplo, `\c` se trata como una `c`.  
  
 **FIN de Específicos de Microsoft**  
  
 Las secuencias de escape permiten enviar caracteres de control no gráficos a un dispositivo de pantalla. Por ejemplo, el carácter ESC (**\033**) se utiliza a menudo como el primer carácter de un comando de control para un terminal o una impresora. Algunas secuencias de escape son específicas del dispositivo. Por ejemplo, las secuencias de escape de tabulación vertical y avance de página (**\v** y **\f**) no afectan al resultado de la presentación, pero realizan las operaciones adecuadas en la impresora.  
  
 También se puede utilizar la barra diagonal inversa (**\\**) como carácter de continuación. Cuando un carácter de nueva línea (equivalente a presionar la tecla ENTRAR) sigue inmediatamente a la barra diagonal inversa, el compilador omite la barra diagonal inversa y el carácter de nueva línea, y trata la línea siguiente como parte de la línea anterior. Esto es útil principalmente para las definiciones del preprocesador que ocupan más de una sola línea. Por ejemplo:  
  
```  
#define assert(exp) \  
( (exp) ? (void) 0:_assert( #exp, __FILE__, __LINE__ ) )  
```  
  
## <a name="see-also"></a>Vea también  
 [Constantes de caracteres de C](../c-language/c-character-constants.md)