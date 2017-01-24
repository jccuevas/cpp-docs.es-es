---
title: "Advertencia del compilador (nivel 3) C4686 | Microsoft Docs"
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
  - "C4686"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4686"
ms.assetid: 767c83c2-9e4b-4f9e-88c8-02128ba563f4
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 3) C4686
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**'**   
 ***tipo definido por el usuario* ': posible cambio de comportamiento, cambio en la convención de llamada devuelta definida por el usuario**  
  
 No se ha definido una especialización de plantilla de clase antes de su utilización en un tipo de valor devuelto.  Nada que crea instancias de la clase resolverá C4686; declarar una instancia de o el acceso a un miembro \(\<\>Cint::anything\) es también opciones.  
  
 Esta advertencia es el resultado del trabajo realizado para que el compilador de Visual C\+\+ .NET 2003 cumpla el estándar ISO C\+\+.  
  
 De forma predeterminada, esta advertencia está desactivada.  Para obtener más información, vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
 En su lugar, pruebe lo siguiente:  
  
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