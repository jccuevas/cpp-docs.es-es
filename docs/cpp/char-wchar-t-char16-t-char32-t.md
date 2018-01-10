---
title: Char, wchar_t, char16_t, char32_t | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- char_cpp
- char16_t_cpp
- wchar_t_cpp
- char32_t_cpp
dev_langs: C++
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c01d4718bbc1781ea4705945bb90874384e09058
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="char-wchart-char16t-char32t"></a>char, wchar_t, char16_t, char32_t
Los tipos char, wchar_t, char16_t y char32_t se compilan en los tipos que representan caracteres alfanuméricos, glifos no alfanuméricos y caracteres no imprimibles. char tiene un tamaño de 8 bits, wchar_t y char16_t de 16, y char32_t de 32.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
char     ch1{ 'a' };    
wchar_t  ch2{ 'a' }; // or {L'a'}    
char16_t ch3{ L'a' };// or {L'a'}    
char32_t ch4{ L'a' };// or {L'a'}  
```  
  
## <a name="remarks"></a>Comentarios  
 El tipo `char` era el tipo de carácter original de C y C++. Puede usarse para almacenar los caracteres de los juegos de caracteres ASCII, ISO-8859 o UTF-8. El tipo `unsigned char` a menudo se usa para representar un *bytes* que no es un tipo integrado en C++. El tipo char no resulta adecuado para el texto en varios idiomas. Por lo general, los programas modernos deben representar texto con uno de los tipos de caracteres anchos. Unicode es el  
  
 En la biblioteca estándar de C++, el tipo basic_string está especializado en cadenas anchas y estrechas. Use std::string con caracteres de tipo char y std::wstring con los de tipo wchar_t. Otros tipos que representan texto, incluidos std::stringstream y std::cout, disponen de especializaciones para cadenas anchas y estrechas.  
  
