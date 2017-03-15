---
title: "Error del compilador C2144 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2144"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2144"
ms.assetid: 49f3959b-324f-4c06-9588-c0ecef5dc5b3
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# Error del compilador C2144
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

error de sintaxis : 'type' debe estar precedido de 'token'  
  
 El compilador esperaba `token` pero, en su lugar, ha encontrado `type`.  
  
 Este error puede deberse a que falte una llave de cierre, un paréntesis de cierre o un punto y coma.  
  
 También puede producirse el error C2144 al intentar crear una macro a partir de una palabra clave de CLR que contenga un carácter de espacio en blanco.  
  
 También puede recibir el error C2144 si está intentando realizar un reenvío de tipos.  Para obtener más información, vea [Reenvío de tipos \(C\+\+\/CLI\)](../../windows/type-forwarding-cpp-cli.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C2144.  
  
```  
// C2144.cpp  
// compile with: /clr /c  
#define REF ref  
REF struct MyStruct0;   // C2144  
  
// OK  
#define REF1 ref struct  
REF1 MyStruct1;  
```  
  
## Ejemplo  
 El ejemplo siguiente genera el error C2144.  
  
```  
// C2144_2.cpp  
// compile with: /clr /c  
ref struct X {  
  
   property double MultiDimProp[,,] {   // C2144  
   // try the following line instead  
   // property double MultiDimProp[int , int, int] {  
      double get(int, int, int) { return 1; }  
      void set(int i, int j, int k, double l) {}  
   }  
  
   property double MultiDimProp2[] {   // C2144  
   // try the following line instead  
   // property double MultiDimProp2[int] {  
      double get(int) { return 1; }  
      void set(int i, double l) {}  
   }  
};  
```