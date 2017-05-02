---
title: "VectorView::First (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorView::First"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorView::First (Método)"
ms.assetid: 543a5c5b-8ce3-4be3-9fad-726928de7855
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorView::First (M&#233;todo)
Devuelve un iterador que especifica el primer elemento del objeto VectorView.  
  
## Sintaxis  
  
```  
  
virtual Windows::Foundation::Collections::IIterator<T>^   
   First();  
```  
  
## Valor devuelto  
 Un iterador que especifica el primer elemento del objeto VectorView.  
  
## Comentarios  
 Una manera cómoda de contener el iterador devuelto por First \(\) es asignar el valor devuelto a una variable que se declare con la palabra clave de deducción de tipos [automática](~/cpp/auto-cpp.md). Por ejemplo: `auto x = myVectorView->First();`.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [VectorView Class](http://msdn.microsoft.com/es-es/79697692-ae58-40e0-958f-cf1be6347994)