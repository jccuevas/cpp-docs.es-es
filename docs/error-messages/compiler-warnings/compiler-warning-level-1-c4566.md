---
title: Compilador advertencia (nivel 1) C4566 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4566
dev_langs: C++
helpviewer_keywords: C4566
ms.assetid: 65f40730-e86f-447c-b37b-16caadcfe311
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7d2755a8e4220f45ef243153b0d0da7b95ec15b4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4566"></a>Advertencia del compilador (nivel 1) C4566
carácter representado por el nombre de carácter universal 'char' no se puede representar en la página de códigos actual (página)  
  
 No todos los caracteres Unicode se pueden representar en la página de códigos ANSI actual.  
  
 Cadenas de caracteres estrechos (caracteres de un byte) se convierten en caracteres multibyte, mientras que no son de cadenas de caracteres anchos (caracteres de dos bytes).  
  
 El ejemplo siguiente genera C4566:  
  
```  
// C4566.cpp  
// compile with: /W1  
int main() {  
   char c1 = '\u03a0';   // C4566  
   char c2 = '\u0642';   // C4566  
  
   wchar_t c3 = L'\u03a0';   // OK  
   wchar_t c4 = L'\u0642';   // OK  
}  
```