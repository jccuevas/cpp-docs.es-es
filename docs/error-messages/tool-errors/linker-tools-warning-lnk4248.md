---
title: "Advertencia de las herramientas del vinculador LNK4248 | Microsoft Docs"
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
  - "LNK4248"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4248"
ms.assetid: e40523ff-e3cb-4ba6-ab79-23f0f339f6cf
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia de las herramientas del vinculador LNK4248
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

símbolo \(token\) de typeref sin resolver \(token\) para 'tipo'; no se puede ejecutar la imagen  
  
 Un tipo no tiene una definición en metadatos de MSIL.  
  
 La advertencia LNK4282 se puede producir cuando sólo hay una declaración adelantada para un tipo en un módulo MSIL \(compilado con **\/clr**\), donde se hace referencia al tipo en el módulo MSIL, y donde el módulo MSIL está vinculado con un módulo nativo que tiene una definición para el tipo.  
  
 En esta situación, el vinculador proporcionará la definición de tipos nativos en los metadatos de MSIL, lo que puede favorecer el comportamiento correcto.  
  
 Sin embargo, si una declaración de tipos adelantada es de tipo CLR, la definición de tipo nativo del vinculador podría no ser correcta.  
  
 Para obtener más información, vea [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
### Para corregir este error  
  
1.  Proporcione la definición de tipos en el módulo MSIL.  
  
## Ejemplo  
 El ejemplo siguiente genera el error LNK4248.  Defina el struct A para resolver.  
  
```  
// LNK4248.cpp  
// compile with: /clr /W1  
// LNK4248 expected  
struct A;  
void Test(A*){}  
  
int main() {  
   Test(0);  
}  
```  
  
## Ejemplo  
 El ejemplo siguiente tiene una definición adelantada de un tipo.  
  
```  
// LNK4248_2.cpp  
// compile with: /clr /c  
class A;   // provide a definition for A here to resolve  
A * newA();  
int valueA(A * a);  
  
int main() {  
   A * a = newA();  
   return valueA(a);  
}  
```  
  
## Ejemplo  
 El ejemplo siguiente genera el error LNK4248.  
  
```  
// LNK4248_3.cpp  
// compile with: /c  
// post-build command: link LNK4248_2.obj LNK4248_3.obj  
class A {  
public:   
   int b;  
};  
  
A* newA() {  
   return new A;  
}  
  
int valueA(A * a) {  
   return (int)a;  
}  
```