---
title: "Error del compilador C2990 | Microsoft Docs"
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
  - "C2990"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2990"
ms.assetid: 674e9f6a-6743-4af0-a7ed-cbe11103a2f8
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2990
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'clase': tipo de no clase ya se declarado como tipo de clase  
  
 La clase que no es de plantilla ni genérica vuelve a definir una clase de plantilla o genérica.  Compruebe si hay conflictos en los archivos de encabezado.  
  
 El código siguiente genera el error C2990:  
  
```  
// C2990.cpp  
// compile with: /c  
template <class T>  
class C{};  
class C{};   // C2990  
```  
  
 El error C2990 también puede producirse cuando se utilizan genéricos:  
  
```  
// C2990b.cpp  
// compile with: /clr /c  
generic <class T>  
ref struct GC;  
  
ref struct GC {};   // C2990  
```  
  
 El error C2990 también puede producirse debido a un cambio importante en el compilador de Visual C\+\+ para Visual C\+\+ 2005; el compilador requiere ahora que varias declaraciones del mismo tipo sean idénticas en relación con la especificación de la plantilla.  
  
 El código siguiente genera el error C2990:  
  
```  
// C2990c.cpp  
// compile with: /c  
template<class T>  
class A;  
  
template<class T>  
struct A2 {  
   friend class A;   // C2990  
};  
  
// OK  
template<class T>  
struct B {  
   template<class T>  
   friend class A;  
};  
```