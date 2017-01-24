---
title: "implementation_only | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "implementation_only"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "implementation_only (atributo)"
ms.assetid: d8cabc86-4425-45a0-9587-d57536980088
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# implementation_only
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de C\+\+**  
  
 Suprime la generación de archivos de encabezado .tlh \(el archivo de encabezado principal\).  
  
## Sintaxis  
  
```  
implementation_only  
```  
  
## Comentarios  
 Este archivo contiene todas las declaraciones utilizadas para exponer el contenido de la biblioteca de tipos.  El archivo de encabezado .tli, con las implementaciones de las funciones miembro del contenedor, se genera y se incluye en la compilación.  
  
 Cuando se especifica este atributo, el contenido del encabezado .tli está en el mismo espacio de nombres que el utilizado normalmente en el encabezado .tlh.  Además, las funciones miembro no se declaran como alineadas.  
  
 El atributo `implementation_only` está destinado a usarse junto con el atributo [no\_implementation](../preprocessor/no-implementation.md) como forma de mantener las implementaciones fuera del archivo de encabezado precompilado \(PCH\).  Una instrucción `#import` con el atributo `no_implementation` se coloca en la región de origen usada para crear el PCH.  Varios archivos de código fuente utilizan el PCH resultante.  Una instrucción `#import` con el atributo `implementation_only` se utiliza entonces fuera de la región de PCH.  Debe usar esta instrucción una sola vez en uno de los archivos de código fuente.  Esto generará todas las funciones miembro del contenedor necesarias sin necesidad de recompilación adicional para cada archivo de código fuente.  
  
> [!NOTE]
>  El atributo `implementation_only` de una instrucción `#import` debe usarse junto con otra instrucción `#import`, de la misma biblioteca de tipos, con el atributo `no_implementation`.  De lo contrario, se generarán errores de compilador.  Esto es porque las definiciones de clase de contenedor generadas por la instrucción `#import` con el atributo `no_implementation` son necesarias para compilar las implementaciones generadas por el atributo `implementation_only`.  
  
 **Específicos de C\+\+: END**  
  
## Vea también  
 [\#import \(Atributos\)](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import \(Directiva\)](../preprocessor/hash-import-directive-cpp.md)