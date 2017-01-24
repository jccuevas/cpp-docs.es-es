---
title: "Objetos de funci&#243;n en STL | Microsoft Docs"
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
  - "functors"
  - "Biblioteca estándar de C++, functors"
  - "Biblioteca estándar de C++, objetos de función"
  - "objetos de función"
ms.assetid: 85f8a735-2c7b-4f10-9c4d-95c666ec4192
caps.latest.revision: 6
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Objetos de funci&#243;n en STL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un *objeto de función*, o *functor*, es cualquier tipo que implementa operator\(\). Este operador se conoce como el *operador de llamada* o a veces el *operador de la aplicación*. La biblioteca de plantillas estándar usa objetos de función principalmente como criterios de ordenación para los contenedores y en algoritmos.  
  
 Los objetos de función proporcionan dos ventajas principales en comparación con una llamada de función sencilla. La primera es que un objeto de función puede contener el estado. La segunda es que un objeto de función es un tipo y, por tanto, puede usarse como un parámetro de plantilla.  
  
## Crear un objeto de función  
 Para crear un objeto de función, cree un tipo e implemente operator\(\), por ejemplo:  
  
```  
class Functor { public: int operator()(int a, int b) { return a < b; } }; int main() { Functor f; int a = 5; int b = 7; int ans = f(a, b); }  
```  
  
 La última línea de la función `main` muestra cómo llamar al objeto de función. Esta llamada es similar a una llamada a una función, pero en realidad llama a operator\(\) del tipo Functor. Esta similitud entre llamar a un objeto de función y una función dio origen al término objeto de función.  
  
## Contenedores y objetos de función  
 La biblioteca de plantillas estándar contiene varios objetos de función en el archivo de encabezado [\<functional\>](../standard-library/functional.md). Uno de los usos de estos objetos de función es como criterio de ordenación para los contenedores. Por ejemplo, el contenedor `set` se declara de la siguiente manera:  
  
```  
template < class Key, class Traits=less<Key>, class Allocator=allocator<Key> > class set  
```  
  
 El segundo argumento de plantilla es el objeto de función `less`. Este objeto de función devuelve `true` si el primer parámetro pasado a este es menor que el segundo parámetro pasado. Puesto que algunos contenedores ordenan sus elementos, el contenedor necesita una manera de comparar dos elementos y esto se consigue mediante el objeto de función. Puede definir sus propios criterios de clasificación para los contenedores mediante la creación de un objeto de función y especificar en la lista de plantillas para el contenedor.  
  
## Algoritmos y objetos de función  
 Otro uso de los objetos de función es en los algoritmos. Por ejemplo, el algoritmo `remove_if` se declara de la siguiente forma:  
  
```  
template<class ForwardIterator, class Predicate> ForwardIterator remove_if( ForwardIterator _First, ForwardIterator _Last, Predicate _Pred );  
```  
  
 El último argumento `remove_if` es un objeto de función que devuelve un valor booleano \(un *predicado*\). Si el resultado del objeto de función es `true`, se quita el elemento del contenedor al que acceden los iteradores `_First` y `_Last`. Puede usar los objetos de función binarios declarados en el encabezado [\<functional\>](../standard-library/functional.md) para el argumento `_Pred` o crear sus propios objetos.  
  
## Vea también  
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)