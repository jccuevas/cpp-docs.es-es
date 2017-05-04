---
title: "end (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Windows::Foundation::Collections::end"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "end (Función)"
ms.assetid: fb837bff-fc76-4bae-9096-facf0e03041c
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# end (Funci&#243;n)
Devuelve un iterador que apunta más allá del final de una colección a la que se tiene acceso con el parámetro de interfaz especificado.  
  
## Sintaxis  
  
```  
  
template <typename T>  
    ::Platform::Collections::VectorIterator<T>   
    end(  
        IVector<T>^ v       );  
  
template <typename T>  
    ::Platform::Collections::VectorViewIterator<T>   
    end(  
        IVectorView<T>^ v  
       );  
template <typename T>   
    ::Platform::Collections::InputIterator<T>   
    end(  
        IIterable<T>^ i  
       );  
  
```  
  
#### Parámetros  
 `T`  
 Un parámetro de tipo de plantilla.  
  
 `v`  
 Una colección de objetos Vector\<T\> o VectorView\<T\> a la que se tiene acceso con una interfaz IVector\<T\> o IVectorView\<T\>.  
  
 `i`  
 Una colección de objetos de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] arbitrarios a los que se tiene acceso con una interfaz IIterable\<T\>.  
  
## Valor devuelto  
 Un iterador que apunta más allá del final de la colección.  
  
## Comentarios  
 Las dos primeras funciones de plantilla devuelven iteradores y la tercera función de plantilla devuelve un iterador de entrada.  
  
 El objeto [Platform::Collections::VectorViewIterator](../cppcx/platform-collections-vectorviewiterator-class.md) devuelto por `end` es un iterador de proxy que almacena elementos de tipo `VectorProxy<T>`. Sin embargo, el objeto proxy casi nunca está visible en el código del usuario. Para obtener más información, consulta [Colecciones \(C\+\+\/CX\)](../cppcx/collections-c-cx.md).  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Windows::Foundation::Collections  
  
## Vea también  
 [Windows::Foundation::Collections \(Espacio de nombres\)](../cppcx/windows-foundation-collections-namespace-c-cx.md)