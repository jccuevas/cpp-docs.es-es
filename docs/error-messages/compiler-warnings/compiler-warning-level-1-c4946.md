---
title: "Advertencia del compilador (nivel 1) C4946 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4946"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4946"
ms.assetid: b85cbef0-e053-4de6-9b14-7b0f82d40495
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Advertencia del compilador (nivel 1) C4946
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se utilizó reinterpret\_cast entre clases relacionadas: 'clase1' y 'clase2'  
  
 No utilice [reinterpret\_cast](../../cpp/reinterpret-cast-operator.md) para convertir entre tipos relacionados.  Utilice [static\_cast](../../cpp/static-cast-operator.md) en su lugar, o de tipos polimórficos, utilice [dynamic\_cast](../../cpp/dynamic-cast-operator.md).  
  
 De forma predeterminada, esta advertencia está desactivada.  Para obtener más información, vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
 El ejemplo de código siguiente genera C4946:  
  
```  
// C4946.cpp  
// compile with: /W1  
#pragma warning (default : 4946)  
class a {  
public:  
   a() : m(0) {}  
   int m;  
};  
  
class b : public virtual a {  
};  
  
class b2 : public virtual a {  
};  
  
class c : public b, public b2 {  
};  
  
int main() {  
   c* pC = new c;  
   a* pA = reinterpret_cast<a*>(pC);   // C4946  
   // try the following line instead  
   // a* pA = static_cast<a*>(pC);  
}  
```