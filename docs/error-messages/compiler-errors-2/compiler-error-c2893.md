---
title: "Error del compilador C2893 | Microsoft Docs"
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
  - "C2893"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2893"
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2893
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

No se pudo especializar la plantilla de función 'nombre de plantilla'  
  
 El compilador no pudo especializar una plantilla de función.  Puede haber muchas causas de este error.  
  
 En general, la manera de solucionar el error 2893 es revisar la firma de la función y asegurarse de que puede crear instancias de cada tipo.  
  
## Ejemplo  
 El error C2893 se debe a que se deduce que el parámetro de plantilla de `f` `T` es `std::map<int,int>`, pero `std::map<int,int>` no tiene un miembro `data_type` \(no se pueden crear instancias de `T::data_type` con `T = std::map<int,int>`\).  El ejemplo siguiente genera el error C2893.  
  
```  
// C2893.cpp  
// compile with: /c /EHsc  
#include<map>  
using namespace std;  
class MyClass {};  
  
template<class T>   
inline typename T::data_type  
// try the following line instead  
// inline typename  T::mapped_type  
f(T const& p1, MyClass const& p2);  
  
template<class T>  
void bar(T const& p1) {  
    MyClass r;  
    f(p1,r);   // C2893  
}  
  
int main() {  
   map<int,int> m;  
   bar(m);  
}  
```