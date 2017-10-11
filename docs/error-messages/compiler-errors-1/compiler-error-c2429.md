---
title: C2429 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2429
dev_langs:
- C++
helpviewer_keywords:
- C2429
ms.assetid: 57ff6df9-5cf1-49f3-8bd8-4e550dfd65a0
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 18fd64199ff043b660bb205199b982ee2843cdcd
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2429"></a>C2429 de Error del compilador
'*característica de lenguaje*'requiere la marca de compilador'*opción del compilador*'  
  
La característica de lenguaje requiere una opción del compilador específico para soporte técnico.  
  
El error C2429: la característica de lenguaje 'anidado de espacio de nombres-definición' requiere la marca de compilador ' / std:c ++ más reciente ' se genera si se intenta definir una *espacio de nombres compuesto*, un espacio de nombres que contiene uno o más nombres de espacio de nombres anidado de ámbito , a partir de Visual Studio 2015 Update 3. Compuesta espacio de nombres no se permiten definiciones en C++ antes de C ++ 17. El compilador admite las definiciones de espacio de nombres compuestos cuando el [/std:c ++ más reciente](../../build/reference/std-specify-language-standard-version.md) se especifica la opción del compilador:  
```cpp  
// C2429a.cpp  
namespace a::b { int i; } // C2429 starting in Visual C++ 2015 Update 3.  
                          // Use /std:c++latest to fix, or do this:  
// namespace a { namespace b { int i; }}  
  
int main() {  
   a::b::i = 2;  
}  
```  
