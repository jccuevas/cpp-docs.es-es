---
title: char, wchar_t, char16_t, char32_t | Microsoft Docs
ms.custom: 
ms.date: 02/14/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- char_cpp
- char16_t_cpp
- wchar_t_cpp
- char32_t_cpp
dev_langs:
- C++
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a87eff9801b2754909159ef4d5e2c24c079ee8f1
ms.sourcegitcommit: 23a0ddd271bbcc31631283542981ff5f1693d27f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2018
---
# <a name="char-wchart-char16t-char32t"></a>char, wchar_t, char16_t, char32_t
Los tipos de **char**, **wchar_t**, **char16_t** y **char32_t** son tipos integrados que representan caracteres alfanuméricos, así como glifos no alfanuméricos y caracteres no imprimibles.

## <a name="syntax"></a>Sintaxis

```cpp  
char     ch1{ 'a' };  // or { u8'a' }   
wchar_t  ch2{ L'a' };    
char16_t ch3{ u'a' };    
char32_t ch4{ U'a' };  
```  
  
## <a name="remarks"></a>Comentarios

El **char** tipo era el tipo de carácter original en C y C++. El tipo **unsigned char** a menudo se usa para representar un *bytes*, que no es un tipo integrado en C++. El **char** tipo puede utilizarse para almacenar los caracteres del juego de caracteres ASCII o cualquiera de los juegos de caracteres ISO-8859 e individuales bytes de caracteres de varios bytes como Shift-JIS o la codificación UTF-8 del juego de caracteres Unicode. Cadenas de **char** tipo se conocen como *restringir* cadenas, incluso cuando se utiliza para codificar los caracteres multibyte. En el compilador de Microsoft, **char** es un tipo de 8 bits.

El **wchar_t** tipo es un tipo de caracteres anchos definido por la implementación. En el compilador de Microsoft, representa un carácter de ancho de 16 bits que usa para almacenar Unicode codificado como UTF-16LE, el tipo de caracteres nativo en sistemas operativos Windows. Las versiones de caracteres anchos de la utilización de las funciones de biblioteca en tiempo de ejecución de C Universal (UCRT) **wchar_t** y su puntero y una matriz de tipos como parámetros y valores devueltos, como las versiones de caracteres anchos de la API nativa de Windows.

El **char16_t** y **char32_t** tipos representan caracteres anchos de 16 bits y 32 bits, respectivamente. Unicode codificado como UTF-16 puede almacenarse en el **char16_t** tipo y Unicode codificados como UTF-32 puede almacenarse en el **char32_t** tipo. Cadenas de estos tipos y **wchar_t** son todo lo que se conoce como *amplia* cadenas, aunque a menudo el término hace referencia específicamente a las cadenas de **wchar_t** tipo.

En la biblioteca estándar de C++, el `basic_string` tipo está especializado en cadenas anchas y estrechas. Use `std::string` cuando son los caracteres de tipo **char**, `std::u16string` cuando son los caracteres de tipo **char16_t**, `std::u32string` cuando son los caracteres de tipo **char32_t** , y `std::wstring` cuando son los caracteres de tipo **wchar_t**. Otros tipos que representan texto, incluidos los `std::stringstream` y `std::cout` disponen de especializaciones para cadenas anchas y estrechas.  
  
