---
title: "Error del compilador C2728 | Microsoft Docs"
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
  - "C2728"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2728"
ms.assetid: 65635f91-1cd1-46e4-9ad7-14726d0546af
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2728
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': una matriz nativa no puede contener este tipo  
  
 Se usó la sintaxis de creación de matrices para crear una matriz de objetos administrados u objetos de WinRT.  No se puede crear una matriz de objetos administrados u objetos de WinRT mediante la sintaxis de matriz nativa.  
  
 Para obtener más información, vea [array](../../windows/arrays-cpp-component-extensions.md).  
  
 El ejemplo siguiente genera el error C2728 y muestra cómo corregirlo:  
  
```  
// C2728.cpp  
// compile with: /clr  
  
int main() {  
   int^ arr[5];   // C2728  
  
   // try the following line instead  
   array<int>^arr2;  
}  
```  
  
 Una matriz [\_\_nogc](../../misc/nogc.md) no puede ser de tipo [\_\_gc](../../misc/gc.md).  
  
 El ejemplo siguiente genera el error C2728 y muestra cómo corregirlo:  
  
```  
// C2728_b.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
int main() {  
   int __gc* arr __nogc[5];   // C2728  
  
   // try the following line instead  
   int arr2 __gc[];  
}  
```