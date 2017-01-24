---
title: "Error del compilador C2899 | Microsoft Docs"
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
  - "C2899"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2899"
ms.assetid: a8942605-5bef-4d1c-b74a-41ae25423b22
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2899
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

typename no se puede utilizar fuera de la declaración de una plantilla  
  
 La palabra clave [typename](../../cpp/typename.md) sólo se puede utilizar en una definición o declaración de plantilla.  En una declaración de plantilla, sólo se puede usar de dos maneras:  
  
```  
// C2899.cpp  
// compile with: /c  
template<typename T>   
class X {};  
  
// Another way  
template<class T>   
struct XX {  
   typename T::A a;   // T::A is a type  
};  
```  
  
 El código siguiente genera el error C2899:  
  
```  
// C2899b.cpp  
// compile with: /c  
struct Y {  
   typedef int B;  
   typename Y::B b;   // C2899  
};  
  
```