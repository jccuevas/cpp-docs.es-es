---
title: "Vector::First (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Vector::First"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Vector::First (Método)"
ms.assetid: ca6b7b55-dd49-4346-bfa4-d8010b228d44
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Vector::First (M&#233;todo)
Devuelve un iterador que apunta al primer elemento del objeto Vector.  
  
## Sintaxis  
  
```  
  
virtual Windows::Foundation::Collections::IIterator <T>^   
   First();  
```  
  
## Valor devuelto  
 Un iterador que apunta al primer elemento del objeto Vector.  
  
## Comentarios  
 Una manera cómoda de contener el iterador devuelto por First \(\) es asignar el valor devuelto a una variable que se declare con la palabra clave de deducción de tipos [automática](~/cpp/auto-cpp.md). Por ejemplo: `auto x = myVector->First();`. El iterador conoce la longitud de la colección.  
  
 Si necesita un par de iteradores para pasar a una función STL, utilice las funciones libres [Windows::Foundation::Collections::begin](../cppcx/begin-function.md) y [Windows::Foundation::Collections::end](../cppcx/end-function.md).  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::Vector \(Clase\)](../cppcx/platform-collections-vector-class.md)   
 [Colecciones](../cppcx/collections-c-cx.md)