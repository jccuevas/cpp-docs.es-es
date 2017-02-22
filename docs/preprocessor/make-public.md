---
title: "make_public | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.make_public"
  - "make_public_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "make_public (pragma)"
  - "pragma (directivas), make_public"
ms.assetid: c3665f4d-268a-4932-9661-c37c8ae6a341
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# make_public
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Indica que un tipo nativo debe tener accesibilidad pública de ensamblado.  
  
## Sintaxis  
  
```  
#pragma make_public(type)  
```  
  
#### Parámetros  
 `type` es el nombre del tipo que desea que tenga accesibilidad pública de ensamblado.  
  
## Comentarios  
 `make_public` es útil cuando el tipo nativo al que se desea hacer referencia es de un archivo .h que no se puede cambiar.  Si desea usar el tipo nativo en signatura de una función pública en un tipo con visibilidad pública de ensamblado, el tipo nativo también debe tener accesibilidad pública de ensamblado o el compilador emitirá una advertencia.  
  
 `make_public` debe especificarse en el ámbito global y solo tiene efecto desde el punto en el que se declara hasta el final del archivo de código fuente.  
  
 El tipo nativo puede ser implícita o explícitamente privado; vea [Visibilidad de tipos](../misc/type-visibility.md) para obtener más información.  
  
## Ejemplo  
 El ejemplo siguiente es el contenido de un archivo .h que contiene las definiciones para dos structs nativos.  
  
```  
// make_public_pragma.h  
struct Native_Struct_1 { int i; };  
struct Native_Struct_2 { int i; };  
```  
  
## Ejemplo  
 El ejemplo de código siguiente utiliza el archivo de encabezado e indica que, a menos que marque explícitamente los structs nativos como públicos usando `make_public`, el compilador generará una advertencia cuando intente usar los structs nativos en la signatura de la función pública en un tipo administrado público.  
  
```  
// make_public_pragma.cpp  
// compile with: /c /clr /W1  
#pragma warning (default : 4692)  
#include "make_public_pragma.h"  
#pragma make_public(Native_Struct_1)  
  
public ref struct A {  
   void Test(Native_Struct_1 u) {u.i = 0;}   // OK  
   void Test(Native_Struct_2 u) {u.i = 0;}   // C4692  
};  
```  
  
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)