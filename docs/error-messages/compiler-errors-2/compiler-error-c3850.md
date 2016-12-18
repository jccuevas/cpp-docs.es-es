---
title: "Error del compilador C3850 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3850"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3850"
ms.assetid: 028f3a37-f3ad-4ebc-9168-3cdea47524d4
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3850
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'char': un nombre de carácter universal especifica un carácter no válido  
  
 Los caracteres representados como nombres de carácter universal deben representar puntos de código Unicode válidos en el rango de 0 a 10FFFF. Un nombre de carácter universal no puede contener un valor en el rango suplente Unicode, de D800 a DFFF ni un par suplente codificado. El compilador genera el par suplente de un punto de código válido automáticamente.  
  
 En el código compilado como C, un nombre de carácter universal no puede representar un carácter del rango de 0000 a 009F, inclusivo, con las excepciones 0024 \('$'\), 0040 \('@'\) y 0060 \('\`'\).  
  
 En el código compilado como C\+\+, un nombre de carácter universal puede usar cualquier punto de código Unicode válido en una cadena o un literal de carácter. Fuera de un literal, un nombre de carácter universal no puede representar un carácter de control en los rangos de 0000 a 001F o de 007F a 009F, ambos inclusivos, ni un miembro del juego de caracteres de origen básico.  Para obtener más información, vea [Juegos de caracteres](../../cpp/character-sets2.md).  
  
## Ejemplo  
 En el ejemplo siguiente se genera el error C3850 y se muestra cómo corregirlo:  
  
```cpp  
// C3850.cpp int main() { int \u0019 = 0;   // C3850, not in allowed range for an identifier const wchar_t * wstr_bad  = L"\UD840DC8A"; // C3850, UCN is surrogate pair const wchar_t * wstr_good = L"\U0002008A"; // Okay, UCN is valid code point }  
```