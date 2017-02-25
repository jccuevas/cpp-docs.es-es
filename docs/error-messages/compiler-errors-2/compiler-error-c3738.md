---
title: "Error del compilador C3738 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3738"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3738"
ms.assetid: dd3ee011-e204-4264-bf3a-da32c4ef7038
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C3738
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'convención de llamada': la convención de llamadas de la creación de instancias explícita debe coincidir con la de la plantilla cuya instancia se está creando  
  
 Se recomienda que no se especifique una convención de llamadas en una creación de instancias explícita.  Pero si debe hacerlo, las convenciones de llamadas deben coincidir.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3738.  
  
```  
// C3738.cpp  
// compile with: /clr  
// processor: x86  
#include <stdio.h>  
template< class T >  
void f ( T arg ) {   // by default calling convention is __cdecl  
   printf ( "f: %s\n", __FUNCSIG__ );  
}  
  
template   
void __stdcall f< int > ( int arg );   // C3738  
// try the following line instead  
// void f< int > ( int arg );  
  
int main () {  
   f(1);  
   f< int > ( 1 );  
}  
```