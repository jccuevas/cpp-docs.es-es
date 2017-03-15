---
title: "C&#243;mo: Sobrecargar funciones con punteros internos y punteros nativos (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Funciones con punteros interiores y nativos, sobrecargar"
ms.assetid: d70df625-4aad-457c-84f5-70a0a290cc1f
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Sobrecargar funciones con punteros internos y punteros nativos (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las funciones pueden sobrecargar dependiendo de si el tipo de parámetro es un puntero interior o puntero nativo.  
  
> [!IMPORTANT]
>  Esta característica de lenguaje es compatible con la opción del compilador **\/clr** , pero no por la opción del compilador **\/ZW** .  
  
## Ejemplo  
  
### Código  
  
```  
// interior_ptr_overload.cpp  
// compile with: /clr  
using namespace System;  
  
// C++ class  
struct S {  
   int i;  
};  
  
// managed class  
ref struct G {  
   int i;  
};  
  
// can update unmanaged storage  
void f( int* pi ) {  
   *pi = 10;  
   Console::WriteLine("in f( int* pi )");  
}  
  
// can update managed storage  
void f( interior_ptr<int> pi ) {  
   *pi = 10;   
   Console::WriteLine("in f( interior_ptr<int> pi )");  
}  
  
int main() {  
   S *pS = new S;   // C++ heap  
   G ^pG = gcnew G;   // common language runtime heap  
   f( &pS->i );  
   f( &pG->i );  
};  
```  
  
### Resultados  
  
```  
in f( int* pi )  
in f( interior_ptr<int> pi )  
```  
  
## Vea también  
 [interior\_ptr \(C\+\+\/CLI\)](../windows/interior-ptr-cpp-cli.md)