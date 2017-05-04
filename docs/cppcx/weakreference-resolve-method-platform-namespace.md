---
title: "WeakReference::Resolve (M&#233;todo, espacio de nombres de la plataforma) | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/WeakReference::Resolve"
ms.assetid: 78bbcadd-89d0-4863-a4e8-1d84040eed7d
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# WeakReference::Resolve (M&#233;todo, espacio de nombres de la plataforma)
Devuelve un identificador a la clase ref original o `nullptr` si el objeto ya no existe.  
  
## Sintaxis  
  
```vb  
  
template<typename T>  
T^ Resolve() const  
```  
  
#### Parámetros  
  
## Valor de propiedad y valor devuelto  
 Identificador de la clase ref a la que se asoció previamente el objeto WeakReference o nullptr.  
  
## Comentarios  
  
## Ejemplo  
 Esta es la descripción de un ejemplo de código.  
  
```  
  
Bar^ bar = ref new Bar(); //use bar... if (bar != nullptr) { WeakReference wr(bar); Bar^ newReference = wr.Resolve<Bar>(); }  
```  
  
 Ten en cuenta que el tipo de parámetro es T, no T^.  
  
## Vea también  
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)