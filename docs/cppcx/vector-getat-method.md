---
title: "Vector::GetAt (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Vector::GetAt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Vector::GetAt (Método)"
ms.assetid: 3766b399-cef2-4006-9a87-50f717390cac
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Vector::GetAt (M&#233;todo)
Recupera el elemento del objeto Vector actual identificado por el índice especificado.  
  
## Sintaxis  
  
```  
  
virtual T GetAt(  
   unsigned int index  
);  
```  
  
#### Parámetros  
 `index`  
 Entero sin signo de base cero que especifica un elemento determinado en el objeto Vector.  
  
## Valor devuelto  
 Elemento especificado por el parámetro `index`. El tipo de elemento se define mediante el typename *T*.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::Vector \(Clase\)](../cppcx/platform-collections-vector-class.md)