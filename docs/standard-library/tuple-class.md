---
title: "tuple (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tr1::tuple"
  - "std.tr1.tuple"
  - "tuple"
  - "tr1.tuple"
  - "std::tr1::tuple"
  - "tuple/std::tr1::tuple"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tuple (clase)"
  - "tuple (clase) [TR1]"
ms.assetid: c38749be-ae4d-41f3-98ea-6aa3250de9a3
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# tuple (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Encapsula una secuencia de longitud fija de elementos.  
  
## Sintaxis  
  
```  
template<class T1, class T2, ..., class TN>  
class tuple {  
public:  
    tuple();  
    explicit tuple(P1, P2, ..., PN);              // 0 < N  
    tuple(const tuple&);  
    template <class U1, class U2, ..., class UN>  
        tuple(const tuple<U1, U2, ..., UN>&);  
    template <class U1, class U2>  
        tuple(const pair<U1, U2>&);               // N == 2  
    void swap(tuple& right);  
    tuple& operator=(const tuple&);  
    template <class U1, class U2, ..., class UN>  
        tuple& operator=(const tuple<U1, U2, ..., UN>&);  
    template <class U1, class U2>  
        tuple& operator=(const pair<U1, U2>&);    // N == 2  
    };  
```  
  
#### Parámetros  
 `TN`  
 El tipo de elemento de la tupla de Enésimo.  
  
## Comentarios  
 La clase de plantilla describe un objeto que almacena objetos n los tipos `T1`, `T2`,…, `TN`, respectivamente, donde donde `0 <= N <= Nmax`.  La extensión de una instancia `tuple<T1, T2, ..., TN>` de tupla es el número `N` de sus argumentos.  El índice del argumento `Ti` de plantilla y de valor almacenado correspondiente de ese tipo es `i - 1`.  Así, mientras que número los tipos desde 1 a n en esta documentación, los valores de índice correspondientes se extendemos desde 0 a n \- 1.  
  
## Ejemplo  
  
```  
// tuple.cpp  
// compile with: /EHsc  
  
#include <vector>  
#include <iomanip>  
#include <iostream>  
#include <tuple>  
#include <string>  
  
using namespace std;  
  
typedef tuple <int, double, string> ids;  
  
void print_ids(const ids& i)  
{  
   cout << "( "  
        << get<0>(i) << ", "   
        << get<1>(i) << ", "   
        << get<2>(i) << " )." << endl;  
}  
  
int main( )  
{  
   // Using the constructor to declare and initialize a tuple  
   ids p1(10, 1.1e-2, "one");  
  
   // Compare using the helper function to declare and initialize a tuple  
   ids p2;  
   p2 = make_tuple(10, 2.22e-1, "two");  
  
   // Making a copy of a tuple  
   ids p3(p1);  
  
   cout.precision(3);  
   cout << "The tuple p1 is: ( ";  
   print_ids(p1);  
   cout << "The tuple p2 is: ( ";  
   print_ids(p2);  
   cout << "The tuple p3 is: ( ";  
   print_ids(p3);  
  
   vector<ids> v;  
  
   v.push_back(p1);  
   v.push_back(p2);  
   v.push_back(make_tuple(3, 3.3e-2, "three"));  
  
   cout << "The tuples in the vector are" << endl;  
   for(vector<ids>::const_iterator i = v.begin(); i != v.end(); ++i)  
   {  
      print_ids(*i);  
   }  
}  
```  
  
  **La tupla p1 es: \(10, 0,011, uno\).**  
**La tupla p2 es: \(10, 0,222, dos\).**  
**La tupla p3 es: \(10, 0,011, uno\).**  
**Las tuplas en el vector son**  
**\(10, 0,011, uno\).**  
**\(10, 0,222, dos\).**  
**\(3, 0,033, tres\).**   
## Requisitos  
 tupla \<de**Encabezado:** \>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<tuple\>](../standard-library/tuple.md)   
 [make\_tuple \(Función\)](../Topic/make_tuple%20Function.md)