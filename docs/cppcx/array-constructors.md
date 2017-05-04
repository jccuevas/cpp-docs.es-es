---
title: "Constructores de matriz | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::Array::Array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Array::Array"
ms.assetid: befb8088-3915-4b5c-b7fd-90f79961412d
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Constructores de matriz
Inicializa una matriz unidimensional modificable de tipos especificados por el parámetro de plantilla de clase, *T*.  
  
## Sintaxis  
  
```  
  
Array(unsigned int size);  
Array(T* data, unsigned int size);  
  
```  
  
#### Parámetros  
 `T`  
 Parámetro de plantilla de clase.  
  
 `size`  
 Número de elementos de la matriz.  
  
 `data`  
 Un puntero a una matriz de datos de tipo `T` que se usa para inicializar este objeto Array.  
  
## Comentarios  
 Para obtener más información sobre cómo crear instancias de Platform::Array, consulta [Array y WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).  
  
## Requisitos  
 **Encabezado:** vccorlib.h  
  
 **Espacio de nombres:** Plataforma  
  
## Vea también  
 [Platform::Array \(Clase\)](../cppcx/platform-array-class.md)