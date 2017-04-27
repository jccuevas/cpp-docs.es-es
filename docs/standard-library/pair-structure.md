---
title: Estructura pair | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- utility/std::pair
- pair
dev_langs:
- C++
helpviewer_keywords:
- pair class
ms.assetid: 539d3d67-80a2-4170-b347-783495d42109
caps.latest.revision: 20
author: corob-msft
ms.author: corob
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
translationtype: Machine Translation
ms.sourcegitcommit: 85c900f2263ae1c1089478badc85388e3b5e8548
ms.openlocfilehash: f9f6574029dd40d0c8c2a2ff2a5f73f4744f5ffe
ms.lasthandoff: 02/24/2017

---
# <a name="pair-structure"></a>pair Structure
Una estructura que proporciona la capacidad de tratar dos objetos como uno solo.  
  
## <a name="syntax"></a>Sintaxis  
```  
struct pair
{
    typedef T1 first_type;
    typedef T2 second_type;
    T1 first;
    T2 second;
    constexpr pair();
    constexpr pair(
        const T1& Val1,
        const T2& Val2);

    template <class Other1, class Other2>
    constexpr pair(const pair<Other1, Other2>& Right);

    template <class Other1, class Other2>
    constexpr pair(const pair <Other1 Val1, Other2 Val2>&& Right);

    template <class Other1, class Other2>
    constexpr pair(Other1&& Val1, Other2&& Val2);
};
```  
#### <a name="parameters"></a>Parámetros  
 `Val1`  
 Valor que inicializa el primer elemento de `pair`.  
  
 `Val2`  
 Valor que inicializa el segundo elemento de `pair`.  
  
 `Right`  
 Un par cuyos valores se deben usar para inicializar los elementos de otro par.  
  
## <a name="return-value"></a>Valor devuelto  
 El primer constructor (predeterminado) inicializa el primer elemento del par en el valor predeterminado del tipo **T1** y el segundo elemento en el valor predeterminado del tipo **T2**.  
  
 El segundo constructor inicializa el primer elemento del par en `Val1` y el segundo en *Val2.*  
  
 El tercer constructor (plantilla) inicializa el primer elemento del par en `Right`. **first** y el segundo en `Right`. **second**.  
  
 El cuarto constructor inicializa el primer elemento del par en `Val1` y el segundo en *Val2* mediante [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
## <a name="remarks"></a>Comentarios  
 La estructura de plantilla almacena un par de objetos de tipo **T1** y **T2** respectivamente. El tipo **first_type** es igual que el parámetro de plantilla **T1** y el tipo **second_type** es igual que el parámetro de plantilla **T2**. Tanto **T1** como **T2** deben proporcionar únicamente un constructor predeterminado, un constructor de argumento único y un destructor. Todos los miembros del tipo `pair` son públicos, porque el tipo se declara como un `struct` en lugar de como una **clase**. Los dos usos más comunes para un par son como tipos devueltos para funciones que devuelven dos valores y como elementos para las clases de contenedor asociativo [map (Clase)](../standard-library/map-class.md) y [multimap (Clase)](../standard-library/multimap-class.md) que tienen una clave y un tipo de valor asociado a cada elemento. Este último cumple los requisitos de un contenedor asociativo de pares y tiene un tipo de valor de la forma `pair`< **const**`key_type`, `mapped_type`>.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// utility_pair.cpp  
// compile with: /EHsc  
#include <utility>  
#include <map>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Using the constructor to declare and initialize a pair  
   pair <int, double> p1 ( 10, 1.1e-2 );  
  
   // Compare using the helper function to declare and initialize a pair  
   pair <int, double> p2;  
   p2 = make_pair ( 10, 2.22e-1 );  
  
   // Making a copy of a pair  
   pair <int, double> p3 ( p1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl;  
  
   // Using a pair for a map element  
   map <int, int> m1;  
   map <int, int>::iterator m1_Iter;  
  
   typedef pair <int, int> Map_Int_Pair;  
  
   m1.insert ( Map_Int_Pair ( 1, 10 ) );  
   m1.insert ( Map_Int_Pair ( 2, 20 ) );  
   m1.insert ( Map_Int_Pair ( 3, 30 ) );  
  
   cout << "The element pairs of the map m1 are:";  
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )  
      cout << " ( " << m1_Iter -> first << ", "  
           << m1_Iter -> second << " )";  
   cout   << "." << endl;  
  
   // Using pair as a return type for a function  
   pair< map<int,int>::iterator, bool > pr1, pr2;  
   pr1 = m1.insert ( Map_Int_Pair ( 4, 40 ) );  
   pr2 = m1.insert ( Map_Int_Pair (1, 10 ) );  
  
   if( pr1.second == true )  
   {  
      cout << "The element (4,40) was inserted successfully in m1."  
           << endl;  
   }  
   else     
   {  
      cout << "The element with a key value of\n"  
           << " ( (pr1.first) -> first ) = " << ( pr1.first ) -> first   
           << " is already in m1,\n so the insertion failed." << endl;  
   }  
  
   if( pr2.second == true )  
   {  
      cout << "The element (1,10) was inserted successfully in m1."  
           << endl;  
   }  
   else     
   {  
      cout << "The element with a key value of\n"  
           << " ( (pr2.first) -> first ) = " << ( pr2.first ) -> first   
           << " is already in m1,\n so the insertion failed." << endl;  
   }  
}  
\* Output:   
The pair p1 is: ( 10, 0.011 ).  
The pair p2 is: ( 10, 0.222 ).  
The pair p3 is: ( 10, 0.011 ).  
The element pairs of the map m1 are: ( 1, 10 ) ( 2, 20 ) ( 3, 30 ).  
The element (4,40) was inserted successfully in m1.  
The element with a key value of  
 ( (pr2.first) -> first ) = 1 is already in m1,  
 so the insertion failed.  
*\  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<utility>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)




