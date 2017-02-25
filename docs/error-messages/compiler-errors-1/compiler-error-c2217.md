---
title: "Error del compilador C2217 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2217"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2217"
ms.assetid: 1ce1e3f5-4171-4376-804d-967f7e612935
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C2217
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'atributo1' requiere 'atributo2'  
  
 El primer atributo de la función requiere la presencia del segundo atributo.  
  
### Posibles causas del error:  
  
1.  La función Interrupt \(`__interrupt`\) se ha declarado como `near`.  Las funciones Interrupt deben ser `far`.  
  
2.  La función Interrupt ha sido declarada con `__stdcall` o `__fastcall`.  Las funciones Interrupt deben utilizar las convenciones de llamada de C.  
  
## Ejemplo  
 El error C2217 también puede producirse si intenta enlazar un delegado a una función CLR que toma un número variable de argumentos.  Si la función también tiene una sobrecarga de matriz de parámetros, utilícela en su lugar.  El ejemplo siguiente genera el error C2217.  
  
```  
// C2217.cpp  
// compile with: /clr  
using namespace System;  
delegate void MyDel(String^, Object^, Object^, ...);   // C2217  
delegate void MyDel2(String ^, array<Object ^> ^);   // OK  
  
int main() {  
   MyDel2^ wl = gcnew MyDel2(Console::WriteLine);  
   array<Object ^ > ^ x = gcnew array<Object ^>(2);  
   x[0] = safe_cast<Object^>(0);  
   x[1] = safe_cast<Object^>(1);  
  
   // wl("{0}, {1}", 0, 1);  
   wl("{0}, {1}", x);  
}  
```