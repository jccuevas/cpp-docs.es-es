---
title: "VectorView::VectorView (Constructor) | Microsoft Docs"
ms.custom: ""
ms.date: "01/25/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorView::VectorView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorView::VectorView (Constructor)"
ms.assetid: 5ec14dbc-5f6f-44b6-8fc4-f5a31053eb5f
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorView::VectorView (Constructor)
Inicializa una nueva instancia de la clase VectorView.  
  
## Sintaxis  
  
```  
VectorView();  
explicit VectorView(  
   UInt32 size  
);  
VectorView(  
   UInt32 size,  
   T value  
);  
explicit VectorView(  
   const ::std::vector<T>& v  
);  
explicit VectorView(  
   ::std::vector<T>&& v  
);  
VectorView(  
   const T * ptr,  
   UInt32 size  
);  
  
template <  
   size_t N  
>  
explicit VectorView(  
   const T (&arr)[N]  
);  
  
template <  
   size_t N  
>  
explicit VectorView(  
   const ::std::array<T,  
   N>& a  
);  
  
explicit VectorView(  
   const ::Platform::Array<T>^ arr  
);  
  
template <  
   typename InIt  
>  
VectorView(  
   InItfirst,  
   InItlast  
);  
  
VectorView(  
   std::initializer_list<T> il  
);  
```  
  
#### Parámetros  
 `InIt`  
 El tipo de una colección de objetos que se utiliza para inicializar el objeto VectorView actual.  
  
 il  
 [std::initializer\_list](../standard-library/initializer-list-class.md) cuyos elementos se usarán para inicializar la clase VectorView.  
  
 `N`  
 El número de elementos en una colección de objetos que se utiliza para inicializar el objeto VectorView actual.  
  
 `size`  
 El número de elementos del objeto VectorView.  
  
 `value`  
 Un valor que se utiliza para inicializar cada elemento en el objeto VectorView actual.  
  
 `v`  
 Un objeto [Lvalues y rvalues](~/cpp/lvalues-and-rvalues-visual-cpp.md) a [::std::vector](../Topic/vector%20Class%201.md) que se usa para inicializar el objeto VectorView actual.  
  
 `ptr`  
 Puntero a un objeto `std::vector` que se usa para inicializar el objeto VectorView actual.  
  
 `arr`  
 Un objeto [Platform::Array](../cppcx/platform-array-class.md) que se usa para inicializar el objeto VectorView actual.  
  
 `a`  
 Un objeto [std::array](../Topic/vector%20Class%201.md) que se usa para inicializar el objeto VectorView actual.  
  
 `first`  
 El primer elemento de una secuencia de objetos que se utilizan para inicializar el objeto VectorView actual. El tipo de `first` se pasa mediante *reenvío directo*. Para obtener más información, consulta [Declarador de referencia a un valor R: &&](~/cpp/rvalue-reference-declarator-amp-amp.md).  
  
 `last`  
 El último elemento de una secuencia de objetos que se utilizan para inicializar el objeto VectorView actual. El tipo de `last` se pasa mediante *reenvío directo*. Para obtener más información, consulta [Declarador de referencia a un valor R: &&](~/cpp/rvalue-reference-declarator-amp-amp.md).  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::Vector \(Clase\)](../cppcx/platform-collections-vector-class.md)