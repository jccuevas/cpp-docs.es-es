---
title: Compilador advertencia (nivel 3) C4686 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4686
dev_langs: C++
helpviewer_keywords: C4686
ms.assetid: 767c83c2-9e4b-4f9e-88c8-02128ba563f4
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 576e714937f0066a7b60ebf38d821715d4157b11
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="compiler-warning-level-3-c4686"></a>Advertencia del compilador (nivel 3) C4686
**'**   
 ***tipo definido por el usuario* ': posible cambio de comportamiento, cambio de UDT devuelta de convención de llamada**  
  
 Una especialización de plantilla de clase no estaba definido antes de se utilizó en un tipo de valor devuelto. Todo lo que crea una instancia de la clase resolverá C4686; declarar una instancia o tiene acceso a un miembro (C\<int >:: nada) también son opciones.  
  
 De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.  
  
 En su lugar, pruebe lo siguiente  
  
```  
// C4686.cpp  
// compile with: /W3  
#pragma warning (default : 4686)  
template <class T>  
class C;  
  
template <class T>  
C<T> f(T);  
  
template <class T>  
class C {};  
  
int main() {  
   f(1);   // C4686  
}  
  
template <class T>  
C<T> f(T) {  
   return C<int>();  
}  
```