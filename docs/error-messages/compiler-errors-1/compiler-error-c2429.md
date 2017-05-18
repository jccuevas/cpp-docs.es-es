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
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: eb0c1bf407d1478451c246cf615d031ef6c45bf9
ms.openlocfilehash: 7d2c27ccdba28720596984c46c9d24f9d29c7b15
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2429"></a>C2429 de Error del compilador
'*característica de lenguaje*'requiere el indicador de compilador'*opción del compilador*'  
  
La característica de idioma requiere una opción específica del compilador para obtener soporte técnico.  
  
El error C2429: la característica de lenguaje 'anidado de namespace-definition' requiere el indicador de compilador ' / std:c ++ más reciente ' se genera si se intenta definir una *espacio de nombres compuesto*, un espacio de nombres que contiene uno o más nombres de espacio de nombres con ámbito anidado, a partir de Visual Studio 2015 Update 3. Compuesta de espacio de nombres no se permiten definiciones en C++ antes de C ++&17;. El compilador admite las definiciones de espacio de nombres compuestos cuando el [/std:c ++ últimas](../../build/reference/std-specify-language-standard-version.md) se especifica la opción del compilador:  
```cpp  
// C2429a.cpp  
namespace a::b { int i; } // C2429 starting in Visual C++ 2015 Update 3.  
                          // Use /std:c++latest to fix, or do this:  
// namespace a { namespace b { int i; }}  
  
int main() {  
   a::b::i = 2;  
}  
```  
