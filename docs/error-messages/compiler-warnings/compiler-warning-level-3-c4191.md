---
title: Compilador advertencia (nivel 3) C4191 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4191
dev_langs:
- C++
helpviewer_keywords:
- C4191
ms.assetid: 576d3bc6-95b7-448a-af31-5d798452df09
caps.latest.revision: 11
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 5cdd66e6318867a7f4df8ff70b6440ae6e7bfa3a
ms.contentlocale: es-es
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-3-c4191"></a>Advertencia del compilador (nivel 3) C4191
'operador/operación': conversión no segura de 'tipo de expresión' a 'tipo necesario'  
  
 Varias operaciones que comprenden punteros a función no se consideran seguras:  
  
-   Los tipos de función con diferentes convenciones de llamada.  
  
-   Los tipos de función con diferentes convenciones de devolución.  
  
-   Los tipos de valor devuelto o argumento con diferentes tamaños, categorías de tipo o clasificaciones.  
  
-   Las longitudes de la lista de argumentos son diferentes (en `__cdecl`, solo en la conversión de una lista más larga a otra más corta, incluso si la más corta es varargs).  
  
-   Puntero a datos (distinto de **void\***) tiene un alias respecto de un puntero a función.  
  
-   Cualquier otra diferencia de tipos que pueda producir un error o una advertencia en `reinterpret_cast`.  
  
 Llamar a esta función a través del puntero de resultados, podría provocar el bloqueo del programa.  
  
 De forma predeterminada, esta advertencia está desactivada. Vea [advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para obtener más información.  
  
 El ejemplo siguiente genera la advertencia C4191:  
  
```  
// C4191.cpp  
// compile with: /W3 /clr  
#pragma warning(default: 4191)  
  
void __clrcall f1() { }  
void __cdecl   f2() { }  
  
typedef void (__clrcall * fnptr1)();  
typedef void (__cdecl   * fnptr2)();  
  
int main() {  
   fnptr1 fp1 = static_cast<fnptr1>(&f1);  
   fnptr2 fp2 = (fnptr2) &f2;  
  
   fnptr1 fp3 = (fnptr1) &f2;   // C4191  
   fnptr2 fp4 = (fnptr2) &f1;   // C4191  
};  
```
