---
title: Compilador advertencia (nivel 1) C4036 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4036
dev_langs:
- C++
helpviewer_keywords:
- C4036
ms.assetid: f0b15359-4d62-48ec-8cb1-a7b36587a47f
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 30ff24d9d8746d914ba4dd098e715d8b5ecb55c9
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4036"></a>Advertencia del compilador (nivel 1) C4036
'type' sin nombre como parámetro real  
  
 No se proporciona ningún nombre de tipo para una estructura, unión, enumeración o clase usada como un parámetro real. Si utilizas [/Zg](../../build/reference/zg-generate-function-prototypes.md) para generar prototipos de función, el compilador emite esta advertencia y desactiva como comentario el parámetro formal en el prototipo generado.  
  
 Especifique un nombre de tipo para resolver esta advertencia.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C4036.  
  
```  
// C4036.c  
// compile with: /Zg /W1  
// D9035 expected  
typedef struct { int i; } T;  
void f(T* t) {}   // C4036  
  
// OK  
typedef struct MyStruct { int i; } T2;  
void f2(T2 * t) {}  
```
