---
title: "Error del compilador C3900 | Microsoft Docs"
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
  - "C3900"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3900"
ms.assetid: a94cc561-8fa8-4344-9e01-e81ff462fae5
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3900
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'miembro': no se permite en el ámbito actual  
  
 Los bloques de propiedades sólo pueden contener declaraciones de función y definiciones de la función inline.  En los bloques de propiedades no se permite ningún miembro que no sea una función.  No se permiten definiciones de tipos, operadores ni funciones friend.  Para obtener más información, vea [propiedad](../../windows/property-cpp-component-extensions.md).  
  
 Las definiciones de eventos sólo pueden contener métodos de acceso y funciones.  
  
 El código siguiente genera el error C3900:  
  
```  
// C3900.cpp  
// compile with: /clr  
ref class X {  
   property int P {  
      void set(int);   // OK  
      int i;   // C3900 variable declaration  
   };  
};  
```  
  
 El código siguiente genera el error C3900:  
  
```  
// C3900b.cpp  
// compile with: /clr  
using namespace System;  
delegate void H();  
ref class X {  
   event H^ E {  
      int m;   // C3900  
  
      // OK  
      void Test() {}  
  
      void add( H^ h ) {}  
      void remove( H^ h ) {}  
      void raise( ) {}  
   }  
};  
```