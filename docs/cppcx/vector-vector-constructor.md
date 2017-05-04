---
title: "Vector::Vector (Constructor) | Microsoft Docs"
ms.custom: ""
ms.date: "01/24/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Vector::Vector"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Vector::Vector (Constructor)"
ms.assetid: 5454433d-e206-45ea-bc8b-bb5a7bf38c17
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Vector::Vector (Constructor)
Inicializa una nueva instancia de la clase Vector.  
  
## Sintaxis  
  
```  
Vector();  
  
explicit Vector(  
    unsigned int size  
    );  
  
Vector(  
    unsigned int size,  
    T value  
    );  
  
template <typename U> explicit Vector(  
    const ::std::vector<U>& v  
    );  
  
template <typename U> explicit Vector(  
    std::vector<U>&& v  
    );  
  
Vector(  
    const T * ptr,  
    unsigned int size  
    );  
  
template <size_t N> explicit Vector(  
    const T(&arr)[N]  
    );  
  
template <size_t N> explicit Vector(  
    const std::array<T, N>& a  
    );  
  
explicit Vector(  
    const Array<T>^ arr  
    );  
  
template <typename InIt> Vector(  
    InIt first,  
    InIt last  
    );  
  
Vector(  
    std::initializer_list<T> il  
    );  
```  
  
#### Parámetros  
 a  
 Un objeto [std::array](../standard-library/array-class-stl.md) que se usa para inicializar la clase Vector.  
  
 a  
 Un objeto [Platform::Array](../cppcx/platform-array-class.md) que se usa para inicializar la clase Vector.  
  
 `InIt`  
 El tipo de una colección de objetos que se utiliza para inicializar el objeto Vector actual.  
  
 il  
 [std::initializer\_list](../standard-library/initializer-list-class.md) de los objetos de tipo `T` que se van a utilizar para inicializar la clase Vector.  
  
 `N`  
 El número de elementos en una colección de objetos que se utiliza para inicializar el objeto Vector actual.  
  
 `size`  
 El número de elementos del objeto Vector.  
  
 `value`  
 Un valor que se utiliza para inicializar cada elemento en el objeto Vector actual.  
  
 `v`  
 [Lvalues y rvalues](~/cpp/lvalues-and-rvalues-visual-cpp.md) a un objeto [::std::vector](../Topic/vector%20Class%201.md) que se usa para inicializar la clase Vector actual.  
  
 `ptr`  
 Puntero a un objeto `std::vector` que se usa para inicializar el objeto Vector actual.  
  
 `arr`  
 Un objeto [Platform::Array](../cppcx/platform-array-class.md) que se usa para inicializar el objeto Vector actual.  
  
 `a`  
 Un objeto [std::array](../Topic/vector%20Class%201.md) que se usa para inicializar el objeto Vector actual.  
  
 `first`  
 El primer elemento de una secuencia de objetos que se utilizan para inicializar el objeto Vector actual. El tipo de `first` se pasa mediante *reenvío directo*. Para obtener más información, consulta [Declarador de referencia a un valor R: &&](~/cpp/rvalue-reference-declarator-amp-amp.md).  
  
 `last`  
 El último elemento de una secuencia de objetos que se utilizan para inicializar el objeto Vector actual. El tipo de `last` se pasa mediante *reenvío directo*. Para obtener más información, consulta [Declarador de referencia a un valor R: &&](~/cpp/rvalue-reference-declarator-amp-amp.md).  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::Vector \(Clase\)](../cppcx/platform-collections-vector-class.md)   
 [Colecciones \(C\+\+\/CX\)](../cppcx/collections-c-cx.md)