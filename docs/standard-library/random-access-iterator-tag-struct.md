---
title: "random_access_iterator_tag (Struct) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "xutility/std::random_access_iterator_tag"
  - "random_access_iterator_tag"
  - "std.random_access_iterator_tag"
  - "std::random_access_iterator_tag"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "random_access_iterator_tag (clase)"
  - "random_access_iterator_tag (struct)"
ms.assetid: 59f5b741-c5b4-459c-ad0a-3b67cddeea23
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# random_access_iterator_tag (Struct)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Clase que proporciona un tipo de valor devuelto para una función **iterator\_category** que representa un iterador de acceso aleatorio.  
  
## Sintaxis  
  
```  
  
   struct random_access_iterator_tag  
: public bidirectional_iterator_tag {};  
```  
  
## Comentarios  
 Las clases de etiquetas de categoría se utilizan como etiquetas de compilación para la selección del algoritmo.  La función de plantilla debe encontrar la categoría más específica del argumento de iterador para poder usar el algoritmo más eficaz en tiempo de compilación.  Para cada iterador de `Iterator`escrito, `iterator_traits`\<`Iterator`\>**::iterator\_category** se debe definir para ser la etiqueta más específica de la categoría que describe el comportamiento del iterador.  
  
 El tipo es igual que **iterator**\<**Iter**\>**::iterator\_category** cuando **Iter** describe un objeto que puede actuar como iterador de acceso aleatorio.  
  
## Ejemplo  
  
```  
// iterator_rait.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
#include <list>  
  
using namespace std;  
  
int main( )  
{  
   vector<int> vi;  
   vector<char> vc;  
   list<char> lc;  
   iterator_traits<vector<int>:: iterator>::iterator_category cati;  
   iterator_traits<vector<char>:: iterator>::iterator_category catc;  
   iterator_traits<list<char>:: iterator>::iterator_category catlc;  
  
   // These are both random-access iterators  
   cout << "The type of iterator for vector<int> is "  
       << "identified by the tag:\n "   
       << typeid ( cati ).name( ) << endl;  
   cout << "The type of iterator for vector<char> is "  
       << "identified by the tag:\n "   
       << typeid ( catc ).name( ) << endl;  
   if ( typeid ( cati ) == typeid( catc ) )  
      cout << "The iterators are the same." << endl << endl;  
   else  
      cout << "The iterators are not the same." << endl << endl;  
  
   // But the list iterator is bidirectinal, not random access  
   cout << "The type of iterator for list<char> is "  
       << "identified by the tag:\n "   
       << typeid (catlc).name( ) << endl;  
  
   // cout << ( typeid ( vi.begin( ) ) == typeid( vc.begin( ) ) ) << endl;  
   if ( typeid ( vi.begin( ) ) == typeid( vc.begin( ) ) )  
      cout << "The iterators are the same." << endl;  
   else  
      cout << "The iterators are not the same." << endl;  
   // A random-access iterator is a bidirectional iterator.  
   cout << ( void* ) dynamic_cast< iterator_traits<list<char>:: iterator>  
          ::iterator_category* > ( &catc ) << endl;  
}  
```  
  
## Resultados del ejemplo  
 El siguiente resultado corresponde a x86.  
  
```  
The type of iterator for vector<int> is identified by the tag:  
 struct std::random_access_iterator_tag  
The type of iterator for vector<char> is identified by the tag:  
 struct std::random_access_iterator_tag  
The iterators are the same.  
  
The type of iterator for list<char> is identified by the tag:  
 struct std::bidirectional_iterator_tag  
The iterators are not the same.  
0012FF3B  
```  
  
## Requisitos  
 **Encabezado:** \<iterator\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [bidirectional\_iterator\_tag \(Struct\)](../standard-library/bidirectional-iterator-tag-struct.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)