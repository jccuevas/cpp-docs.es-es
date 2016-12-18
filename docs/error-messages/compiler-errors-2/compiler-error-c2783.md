---
title: "Error del compilador C2783 | Microsoft Docs"
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
  - "C2783"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2783"
ms.assetid: 1ce94a11-bb8b-4be3-a222-f1f105da74b3
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2783
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'declaración' : no se pudo deducir el argumento de plantilla para 'identificador'  
  
 El compilador no pudo determinar un argumento de plantilla.  No se pueden utilizar argumentos predeterminados para deducir un argumento de plantilla.  
  
 El código siguiente genera el error C2783:  
  
```  
// C2783.cpp  
template<typename T1, typename T2>  
T1 f(T2) {  
   return 248;  
}  
  
int main() {  
   f(1);   // C2783  
   // try the following line instead  
   int i = f<int>(1);  
}  
```  
  
 El error C2783 también puede producirse al utilizar clases genéricas:  
  
```  
// C2783b.cpp  
// compile with: /clr  
using namespace System;  
generic<typename T1, typename T2>   
T1 gf(T2) {  
   T1 t1 = safe_cast<T1>( Activator::CreateInstance(T1::typeid));  
   return t1;  
}  
  
ref class MyClass{};  
  
int main() {  
   int i;  
   i = gf(9);   // C2783  
  
   // OK  
   i = gf<int>(9);  
}  
```