---
title: "Error del compilador C2690 | Microsoft Docs"
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
  - "C2690"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2690"
ms.assetid: f165a806-14bd-4942-99b7-8a9fc7dea227
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2690
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator': no se puede realizar aritmética de puntero en una matriz de WinRT  
  
 La aritmética de puntero no se permite en una matriz administrada o de WinRT.  Use la notación de índice de matriz para recorrer la matriz.  
  
 **Extensiones administradas de C\+\+**  
  
 La aritmética de puntero no se permite en una matriz [\_\_gc](../../misc/gc.md).  Use la notación de índice de matriz para recorrer la matriz.  
  
 El siguiente ejemplo genera el error C2690:  
  
```  
// C2690b.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
int main() {  
   String* x[] = new String*[10];  
   x[0] = "test";  
   Console::WriteLine(x[0]);  
   x++;   // C2690  
}  
```