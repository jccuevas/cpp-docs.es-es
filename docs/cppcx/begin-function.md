---
title: "begin (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Windows::Foundation::Collections::begin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "begin (Función)"
ms.assetid: 5a44fb33-e247-49fd-b7a1-4a5b42e9e1e4
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# begin (Funci&#243;n)
Devuelve un iterador que apunta al principio de una colección a la que se tiene acceso con el parámetro de interfaz especificado.  
  
## Sintaxis  
  
```  
  
template <typename T>   
    ::Platform::Collections::VectorIterator<T>   
    begin(  
          IVector<T>^ v         );  
  
template <typename T>   
    ::Platform::Collections::VectorViewIterator<T>   
    begin(  
          IVectorView<T>^ v  
         );   
  
template <typename T>   
    ::Platform::Collections::InputIterator<T>   
    begin(  
          IIterable<T>^ i         );  
  
```  
  
#### Parámetros  
 `T`  
 Un parámetro de tipo de plantilla.  
  
 `v`  
 Una colección de objetos Vector\<T\> o VectorView\<T\> a la que se tiene acceso con una interfaz IVector\<T\> o IVectorView\<T\>.  
  
 `i`  
 Una colección de objetos de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] arbitrarios a los que se tiene acceso con una interfaz IIterable\<T\>.  
  
## Valor devuelto  
 Un iterador que apunta al principio de la colección.  
  
## Comentarios  
 Las dos primeras funciones de plantilla devuelven iteradores y la tercera función de plantilla devuelve un iterador de entrada.  
  
 El objeto VectorIterator devuelto por begin es un iterador de proxy que almacena los elementos de tipo VectorProxy\<T\>. Sin embargo, el objeto proxy casi nunca está visible en el código del usuario. Para obtener más información, consulta [Colecciones \(C\+\+\/CX\)](../cppcx/collections-c-cx.md).  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Windows::Foundation::Collections  
  
## Vea también  
 [Windows::Foundation::Collections \(Espacio de nombres\)](../cppcx/windows-foundation-collections-namespace-c-cx.md)