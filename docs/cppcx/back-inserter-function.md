---
title: "back_inserter (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Windows::Foundation::Collections::back_inserter"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "back_inserter (Función)"
ms.assetid: 91476338-5548-44b7-bc7e-2150f4fbe31a
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# back_inserter (Funci&#243;n)
Devuelve un iterador que se utiliza para insertar elementos en el final de la colección especificada.  
  
## Sintaxis  
  
```  
  
template <  
   typename T  
   >  
   ::Platform::BackInsertIterator<T>   
    back_inserter(  
                  IVector<T>^ v  
                 );  
  
template <  
   typename T  
   >  
   ::Platform::BackInsertIterator<T>   
   back_inserter(  
                IObservableVector<T>^ v  
                );  
```  
  
#### Parámetros  
 `T`  
 Un parámetro de tipo de plantilla.  
  
 `v`  
 Un puntero de interfaz que proporciona acceso a la colección subyacente.  
  
## Valor devuelto  
 Un iterador.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Windows::Foundation::Collections  
  
## Vea también  
 [Windows::Foundation::Collections \(Espacio de nombres\)](../cppcx/windows-foundation-collections-namespace-c-cx.md)