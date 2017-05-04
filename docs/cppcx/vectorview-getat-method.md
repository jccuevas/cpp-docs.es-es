---
title: "VectorView::GetAt (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorView::GetAt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorView::GetAt (Método)"
ms.assetid: 01c5feda-2a97-4429-ae15-4aced96ce332
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorView::GetAt (M&#233;todo)
Recupera el elemento del objeto VectorView actual indicado por el índice especificado.  
  
## Sintaxis  
  
```  
  
T GetAt(  
   UInt32 index  
);  
```  
  
#### Parámetros  
 `index`  
 Entero sin signo de base cero que especifica un elemento determinado en el objeto VectorView.  
  
## Valor devuelto  
 Elemento especificado por el parámetro `index`. El tipo de elemento se especifica por el parámetro de plantilla VectorView *T*.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [VectorView Class](http://msdn.microsoft.com/es-es/79697692-ae58-40e0-958f-cf1be6347994)