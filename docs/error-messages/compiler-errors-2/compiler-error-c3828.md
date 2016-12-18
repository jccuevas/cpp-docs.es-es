---
title: "Error del compilador C3828 | Microsoft Docs"
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
  - "C3828"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3828"
ms.assetid: 8d9cee75-9504-4bc8-88b6-2413618a3f45
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3828
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'object type': no se permiten argumentos de ubicación mientras se crean instancias de clases WinRT o administradas  
  
 Al crear un objeto de un tipo administrado o en tiempo de ejecución de Windows, no puede utilizar el formato de ubicación del operador [ref new, gcnew](../../windows/ref-new-gcnew-cpp-component-extensions.md) o [nueva](../../cpp/new-operator-cpp.md).  
  
 El ejemplo siguiente genera el error C3828 y muestra cómo corregirlo:  
  
```  
// C3828a.cpp  
// compile with: /clr  
ref struct M {  
};  
  
ref struct N {  
   static array<char>^ bytes = gcnew array<char>(256);  
};  
  
int main() {  
   M ^m1 = new (&N::bytes) M();   // C3828  
   // The following line fixes the error.  
   // M ^m1 = gcnew M();  
}  
```