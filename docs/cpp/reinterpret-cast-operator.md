---
title: reinterpret_cast (operador) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- reinterpret_cast
- reinterpret_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- reinterpret_cast keyword [C++]
ms.assetid: eb3283c7-7f88-467e-affd-407d37b46d6c
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 71218dc713b24669dc1648b748a0326da0c03152
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="reinterpretcast-operator"></a>reinterpret_cast (Operador)
Permite que cualquier puntero se convierta en cualquier otro tipo de puntero. También permite convertir cualquier tipo entero en cualquier tipo de puntero y viceversa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
reinterpret_cast < type-id > ( expression )  
```  
  
## <a name="remarks"></a>Comentarios  
 El uso incorrecto del operador `reinterpret_cast` puede ser no seguro. A menos que la conversión deseada sea inherentemente de bajo nivel, se debe utilizar uno de los otros operadores de conversión.  
  
 El operador `reinterpret_cast` se puede utilizar para las conversiones como `char*` a `int*` o `One_class*` a `Unrelated_class*`, que son intrínsecamente no seguras.  
  
 El resultado de `reinterpret_cast` no se puede utilizar con seguridad para algo distinto que convertirlo otra vez a su tipo original. Otros usos son, en el mejor de los casos, no portables.  
  
 El `reinterpret_cast` operador no puede desechar la **const**, `volatile`, o **__unaligned** atributos. Vea [const_cast (operador)](../cpp/const-cast-operator.md) para obtener información acerca de cómo quitar estos atributos.  
  
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
  
 `reinterpret_cast` permite que el puntero se tratará como tipo entero. El resultado se cambia a bits y se compara mediante XOR consigo mismo para producir un índice único (con un alto grado de probabilidad). El índice se trunca mediante una conversión de estilo de C al tipo de valor devuelto de la función.  
  
## <a name="see-also"></a>Vea también  
 [Operadores de conversión](../cpp/casting-operators.md)   
 [Palabras clave](../cpp/keywords-cpp.md)
