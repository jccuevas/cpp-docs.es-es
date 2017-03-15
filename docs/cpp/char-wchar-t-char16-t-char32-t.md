---
title: "char, wchar_t, char16_t, char32_t | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "char_cpp"
  - "char16_t_cpp"
  - "whchar_t_cpp"
  - "char32_t_cpp"
dev_langs: 
  - "C++"
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
caps.latest.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 2
---
# char, wchar_t, char16_t, char32_t
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los tipos char, wchar\_t, char16\_t y char32\_t se compilan en los tipos que representan caracteres alfanuméricos, glifos no alfanuméricos y caracteres no imprimibles.  char tiene un tamaño de 8 bits, wchar\_t y char16\_t de 16, y char32\_t de 32.  
  
## Sintaxis  
  
```vb  
char     ch1{ 'a' };  
wchar_t  ch2{ 'a' }; // or {L'a'}  
char16_t ch3{ L'a' };// or {L'a'}  
char32_t ch4{ L'a' };// or {L'a'}  
```  
  
## Comentarios  
 El tipo `char` era el tipo de carácter original de C y C\+\+.  Puede usarse para almacenar los caracteres de los juegos de caracteres ASCII, ISO\-8859 o UTF\-8.  El tipo `unsigned char` se usa a menudo para representar un *byte* que no corresponde a un tipo integrado en C\+\+.  El tipo char no resulta adecuado para el texto en varios idiomas.  Por lo general, los programas modernos deben representar texto con uno de los tipos de caracteres anchos.  Unicode es el  
  
 En la biblioteca estándar de C\+\+, el tipo basic\_string está especializado en cadenas anchas y estrechas.  Use std::string con caracteres de tipo char y std::wstring con los de tipo wchar\_t.  Otros tipos que representan texto, incluidos std::stringstream y std::cout, disponen de especializaciones para cadenas anchas y estrechas.  
  
## Requisitos