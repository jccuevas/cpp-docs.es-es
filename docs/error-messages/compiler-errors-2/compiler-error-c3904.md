---
title: "Error del compilador C3904 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3904"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3904"
ms.assetid: 08297605-e4f2-4c6c-b637-011f1fd40631
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Error del compilador C3904
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'descriptor\_de\_acceso\_de\_propiedad': debe especificar número parámetros  
  
 Compruebe el número de parámetros de los métodos `get` y `set` con respecto a las dimensiones de la propiedad.  
  
-   El número de parámetros del método `get` debe ser igual al número de dimensiones de la propiedad, o cero en el caso de las propiedades no indizadas.  
  
-   El número de parámetros del método `set` debe superar en una unidad al número de dimensiones de la propiedad.  
  
 Para obtener más información, vea [propiedad](../../windows/property-cpp-component-extensions.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3904.  
  
```  
// C3904.cpp  
// compile with: /clr /c  
ref class X {  
   property int P {  
      // set  
      void set();   // C3904  
      // try the following line instead  
      // void set(int);  
  
      // get  
      int get(int, int);   // C3904  
      // try the following line instead  
      // int get();  
   };  
};  
```  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3904.  
  
```  
// C3904b.cpp  
// compile with: /clr /c  
ref struct X {  
   property int Q[double, double, float, float, void*, int] {  
      // set  
      void set(double, void*);   // C3904  
      // try the following line instead  
      // void set(double, double, float, float, void*, int, int);  
  
      // get  
      int get();   // C3904  
      // try the following line instead  
      // int get(double, double, float, float, void*, int);  
   }  
};  
```