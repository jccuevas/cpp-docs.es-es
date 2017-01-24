---
title: "Error del compilador C3798 | Microsoft Docs"
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
  - "C3798"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3798"
ms.assetid: b2f8b1d8-8812-49b8-a346-28e48f02ba5c
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3798
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'especificador': la declaración de propiedad no puede tener un especificador de reemplazo \(en su lugar, se debe colocar en los métodos get o set de propiedad\)  
  
 Se ha declarado incorrectamente una propiedad.  Para obtener más información, vea  
  
-   [propiedad](../../windows/property-cpp-component-extensions.md)  
  
-   [abstractas](../../windows/abstract-cpp-component-extensions.md)  
  
-   [sellado](../../windows/sealed-cpp-component-extensions.md)  
  
## Ejemplo  
 El ejemplo siguiente genera C3798:  
  
```  
// C3798.cpp  
// compile with: /clr /c  
ref struct A {  
   property int Prop_1 abstract;   // C3798  
   property int Prop_2 sealed;   // C3798  
  
   // OK  
   property int Prop_3 {  
      virtual int get() abstract;  
      virtual void set(int i) abstract;  
   }  
  
   property int Prop_4 {  
      virtual int get() sealed;  
      virtual void set(int i) sealed;  
   }  
};  
```