---
title: "Advertencia del compilador (nivel 1) C4544 | Microsoft Docs"
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
  - "C4544"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4544"
ms.assetid: 11ee04df-41ae-435f-af44-881e801315a8
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4544
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'declaration': se omitió el argumento de plantilla predeterminado de esta declaración de plantilla  
  
 Se especificó un argumento de plantilla predeterminado en una ubicación incorrecta y se omitió.  Un argumento de plantilla predeterminado de una plantilla de clase solo puede especificarse en la declaración o definición de la plantilla de clase y no en un miembro de la plantilla de clase.  
  
 Este ejemplo genera el error C4545 y el ejemplo siguiente muestra cómo corregirlo:  
  
```  
// C4544.cpp  
// compile with: /W1 /LD  
template <class T>   
struct S  
{  
   template <class T1>   
      struct S1;  
   void f();  
};  
  
template <class T=int>  
template <class T1>  
struct S<T>::S1 {};   // C4544  
```  
  
 En este ejemplo, el parámetro predeterminado se aplica a la plantilla de clase `S`:  
  
```  
// C4544b.cpp  
// compile with: /LD  
template <class T = int>   
struct S  
{  
   template <class T1>   
      struct S1;  
   void f();  
};  
  
template <class T>  
template <class T1>  
struct S<T>::S1 {};  
```