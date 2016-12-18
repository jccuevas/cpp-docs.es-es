---
title: "Error del compilador C2975 | Microsoft Docs"
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
  - "C2975"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2975"
ms.assetid: 526f6b9d-6c76-4c12-9252-1b1d7c1e06c7
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2975
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'arg' : argumento de plantilla no válido para 'tipo', se esperaba una expresión constante evaluable en tiempo de compilación  
  
 El argumento de plantilla no coincide con la declaración de plantilla; debe aparecer una expresión constante dentro de los paréntesis angulares.  No se permiten las variables como argumentos de plantilla.  Compruebe la definición de plantilla para encontrar los tipos adecuados.  
  
 El código siguiente genera el error C2975:  
  
```  
// C2975.cpp  
template<int I>  
class X {};  
  
int main() {  
   int i = 4, j = 2;  
   X<i + j> x1;   // C2975  
   X<6> x2;   // OK  
}  
```  
  
 También se producirá el error C2975 cuando se utilice \_\_LINE\_\_ como constante en tiempo de compilación con [\/ZI](../../build/reference/z7-zi-zi-debug-information-format.md).  Una solución sería compilar con [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) en lugar de **\/ZI**.  
  
```  
// C2975b.cpp  
// compile with: /ZI  
// processor: x86  
template<long line>   
void test(void) {}  
  
int main() {  
   test<__LINE__>();   // C2975  
}  
```