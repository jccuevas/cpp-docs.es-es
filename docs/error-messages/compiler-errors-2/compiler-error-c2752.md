---
title: "Error del compilador C2752 | Microsoft Docs"
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
  - "C2752"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2752"
ms.assetid: ae42b3ec-84a9-4e9d-8d59-3d208132d0b2
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2752
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'plantilla' : hay más de una coincidencia de especialización parcial en la lista de argumentos de plantilla  
  
 Se ha creado una instancia de forma ambigua.  
  
 El código siguiente genera el error C2752:  
  
```  
// C2752.cpp  
template<class T, class U>   
struct A {};  
  
template<class T, class U>   
struct A<T*, U> {};  
  
template<class T, class U>   
struct A<T,U*> {};  
  
// try the following line instead  
// template<class T, class U> struct A<T*,U*> {};  
  
int main() {  
   A<char*,int*> a;   // C2752 an instantiation  
  
   // OK  
   A<char*,int> a1;  
   A<char,int*> a2;  
   A<char,int> a3;  
}  
```