---
title: "Platform::Array (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::Array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Array (Clase)"
ms.assetid: 7815ab40-88c5-42b0-83b8-081cef0cda31
caps.latest.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 9
---
# Platform::Array (Clase)
Representa una matriz unidimensional modificable que se puede recibir y pasar a través de la interfaz binaria de aplicación \(ABI\).  
  
## Sintaxis  
  
```cpp  
  
template <typename T>  
    private ref class Array<TArg,1> :   
         public WriteOnlyArray<TArg, 1>,  
         public IBoxArray<TArg>  
  
```  
  
## Miembros  
 Platform::Array hereda todos sus métodos de [Platform::WriteOnlyArray \(Clase\)](../cppcx/platform-writeonlyarray-class.md) e implementa la propiedad `Value` de [Platform::IBoxArray \(Interfaz\)](../cppcx/platform-iboxarray-interface.md).  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[Constructores de matriz](../cppcx/array-constructors.md)|Inicializa una matriz unidimensional modificable de tipos especificados por el parámetro de plantilla de clase, *T*.|  
  
### Métodos  
 Vea [Platform::WriteOnlyArray \(Clase\)](../cppcx/platform-writeonlyarray-class.md).  
  
### Propiedades  
  
|||  
|-|-|  
|[Array::Value \(Propiedad\)](../cppcx/array-value-property.md)|Recupera un identificador a la matriz actual.|  
  
## Comentarios  
 La clase Array está sellada y no se puede heredar.  
  
 El sistema de tipos de Windows en tiempo de ejecución no admite el concepto de matrices escalonadas y, por consiguiente, no se puede pasar un IVector\<Platform::Array\<T\>\> como valor devuelto o parámetro del método. Para pasar una matriz escalonada o un grupo de secuencias a través de la ABI, usa `IVector<IVector<T>^>`.  
  
 Para obtener más información sobre cuándo y cómo usar Platform::Array, consulta [Array y WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).  
  
 El sistema de tipos de Windows en tiempo de ejecución no admite el concepto de matrices escalonadas y, por consiguiente, no se puede pasar un IVector\<Platform::Array\<T\>\> como valor devuelto o parámetro del método. Para pasar una matriz escalonada o un grupo de secuencias a través de la ABI, usa `IVector<IVector<T>^>`.  
  
 Esta clase se define en el encabezado de vccorlib.h, que se incluye automáticamente por el compilador. Es visible en IntelliSense pero no en el Examinador de objetos porque no es un tipo público definido en platform.winmd.  
  
## Requisitos  
 Opción del compilador: **\/ZW**  
  
## Vea también  
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)   
 [Array y WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)