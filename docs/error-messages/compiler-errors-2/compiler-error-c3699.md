---
title: "Error del compilador C3699 | Microsoft Docs"
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
  - "C3699"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3699"
ms.assetid: 47c29afc-ab8b-4238-adfe-788dd6e00b3b
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3699
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operador' : no se puede utilizar este direccionamiento indirecto en el tipo 'tipo'  
  
 Se ha intentado utilizar un direccionamiento indirecto no permitido en `type`.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3699.  
  
```  
// C3699.cpp  
// compile with: /clr /c  
using namespace System;  
int main() {  
   String * s;   // C3699  
   // try the following line instead  
   // String ^ s2;  
}  
```  
  
## Ejemplo  
 Una propiedad trivial no puede tener tipo de referencia.  Para obtener más información, vea [propiedad](../../windows/property-cpp-component-extensions.md).  El ejemplo siguiente genera el error C3699.  
  
```  
// C3699_b.cpp  
// compile with: /clr /c  
ref struct C {  
   property System::String % x;   // C3699  
   property System::String ^ y;   // OK  
};  
```  
  
## Ejemplo  
 El equivalente de la sintaxis de un "puntero a un puntero" es un identificador a una referencia de seguimiento.  El ejemplo siguiente genera el error C3699.  
  
```  
// C3699_c.cpp  
// compile with: /clr /c  
using namespace System;  
void Test(String ^^ i);   // C3699  
void Test2(String ^% i);  
```