---
title: "reinterpret_cast (Operador) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "reinterpret_cast"
  - "reinterpret_cast_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reinterpret_cast (palabra clave) [C++]"
ms.assetid: eb3283c7-7f88-467e-affd-407d37b46d6c
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# reinterpret_cast (Operador)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Permite que cualquier puntero se convierta en cualquier otro tipo de puntero.  También permite convertir cualquier tipo entero en cualquier tipo de puntero y viceversa.  
  
## Sintaxis  
  
```  
reinterpret_cast < type-id > ( expression )  
```  
  
## Comentarios  
 El uso incorrecto del operador `reinterpret_cast` puede ser no seguro.  A menos que la conversión deseada sea inherentemente de bajo nivel, se debe utilizar uno de los otros operadores de conversión.  
  
 El operador `reinterpret_cast` se puede utilizar para las conversiones como `char*` a `int*` o `One_class*` a `Unrelated_class*`, que son intrínsecamente no seguras.  
  
 El resultado de `reinterpret_cast` no se puede utilizar con seguridad para algo distinto que convertirlo otra vez a su tipo original.  Otros usos son, en el mejor de los casos, no portables.  
  
 El operador `reinterpret_cast` no puede deshacer la conversión de los atributos **const**, `volatile` o **\_\_unaligned**.  Vea [const\_cast \(Operador\)](../cpp/const-cast-operator.md) para obtener información sobre cómo quitar estos atributos.  
  
 El operador `reinterpret_cast` convierte un valor de puntero NULL al valor de puntero NULL del tipo de destino.  
  
 Un uso práctico de `reinterpret_cast` es el que se hace en una función hash, que asigna un valor a un índice de tal forma que dos valores distintos raramente acaben teniendo el mismo índice.  
  
```  
#include <iostream>  
using namespace std;  
  
// Returns a hash code based on an address  
unsigned short Hash( void *p ) {  
   unsigned int val = reinterpret_cast<unsigned int>( p );  
   return ( unsigned short )( val ^ (val >> 16));  
}  
  
using namespace std;  
int main() {  
   int a[20];  
   for ( int i = 0; i < 20; i++ )  
      cout << Hash( a + i ) << endl;  
}  
  
Output:   
64641  
64645  
64889  
64893  
64881  
64885  
64873  
64877  
64865  
64869  
64857  
64861  
64849  
64853  
64841  
64845  
64833  
64837  
64825  
64829  
```  
  
 `reinterpret_cast` permite que el puntero se tratará como tipo entero.  El resultado se cambia a bits y se compara mediante XOR consigo mismo para producir un índice único \(con un alto grado de probabilidad\).  El índice se trunca mediante una conversión de estilo de C al tipo de valor devuelto de la función.  
  
## Vea también  
 [Operadores de conversión](../cpp/casting-operators.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)