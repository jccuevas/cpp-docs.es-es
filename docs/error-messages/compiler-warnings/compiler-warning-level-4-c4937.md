---
title: Compilador advertencia (nivel 4) C4937 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4937
dev_langs:
- C++
helpviewer_keywords:
- C4937
ms.assetid: 2bb9f0e7-bbd6-4697-84de-95955e32ae29
caps.latest.revision: 7
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
ms.openlocfilehash: 655bf5154f66e2f641321adbd395c2bc5694e148
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-4-c4937"></a>Advertencia del compilador (nivel 4) C4937
'texto1' y 'texto2' no se pueden distinguir como argumentos para 'directiva'  
  
 Debido a la forma en que el compilador procesa argumentos para directivas, no es posible distinguir los nombres que tienen un significado para el compilador como, por ejemplo, palabras clave con varias representaciones de texto (en formato de subrayado simple y doble).  
  
 Algunos ejemplos de estas cadenas son __cdecl y \__forceinline.  Tenga en cuenta que con /Za solo se habilita el formato de subrayado doble.  
  
 El ejemplo siguiente genera la advertencia C4937:  
  
```  
// C4937.cpp  
// compile with: /openmp /W4  
#include "omp.h"  
int main() {  
   #pragma omp critical ( __leave )   // C4937  
   ;  
  
   // OK  
   #pragma omp critical ( leave )  
   ;  
}  
```
