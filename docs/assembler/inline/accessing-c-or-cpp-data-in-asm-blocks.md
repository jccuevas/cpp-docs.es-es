---
title: "Acceso a datos de C o C++ en bloques __asm | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__asm (palabra clave) [C++], miembros de datos"
  - "acceso a datos [C++], en bloques __asm"
  - "miembros de datos [C++], en bloques __asm"
  - "tipos de estructuras en bloques __asm"
ms.assetid: e99f5a28-0381-4090-8ece-6af8f2436a49
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Acceso a datos de C o C++ en bloques __asm
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 Una gran ventaja del ensamblado insertado es la capacidad de hacer referencia a variables de C o C\+\+ por nombre.  Un bloque `__asm` puede hacer referencia a cualquier símbolo, incluidos los nombres de variables que esté en el ámbito donde aparece el bloque.  Por ejemplo, si la variable C `var` está en el ámbito, la instrucción  
  
```  
__asm mov eax, var  
```  
  
 almacena el valor de `var` en EAX.  
  
 Si una clase, estructura o unión tiene un nombre único, un bloque `__asm` puede hacer referencia al mismo solo con el nombre de miembro, sin especificar el nombre de variable o `typedef` antes que el operador de punto \(**.**\).  Si el nombre de miembro no es único, sin embargo, debe colocar una variable o un nombre `typedef` inmediatamente antes del operador de punto.  Por ejemplo, los tipos de estructura del ejemplo siguiente comparten `same_name` como nombre de miembro:.  
  
 Si declara variables con los tipos  
  
```  
struct first_type hal;  
struct second_type oat;  
```  
  
 todas las referencias al miembro `same_name` deben utilizar el nombre de variable porque `same_name` no es único.  Pero el miembro `weasel` tiene un nombre único, por lo que se puede hacer referencia al mismo usando únicamente el nombre del miembro:  
  
```  
// InlineAssembler_Accessing_C_asm_Blocks.cpp  
// processor: x86  
#include <stdio.h>  
struct first_type  
{  
   char *weasel;  
   int same_name;  
};  
  
struct second_type  
{  
   int wonton;  
   long same_name;  
};  
  
int main()  
{  
   struct first_type hal;  
   struct second_type oat;  
  
   __asm  
   {  
      lea ebx, hal  
      mov ecx, [ebx]hal.same_name ; Must use 'hal'  
      mov esi, [ebx].weasel       ; Can omit 'hal'  
   }  
   return 0;  
}  
```  
  
 Observe que la omisión del nombre de variable es cuestión simplemente de comodidad de codificación.  Se generan las mismas instrucciones de ensamblado tanto si el nombre de variable está presente como si no.  
  
 Puede tener acceso a los miembros de datos de C\+\+ sin tener en cuenta las restricciones de acceso.  Sin embargo, no se puede llamar a funciones miembro.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Usar C o C\+\+ en bloques \_\_asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)