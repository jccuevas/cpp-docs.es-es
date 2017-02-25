---
title: "Cu&#225;ndo precompilar c&#243;digo fuente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "pch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "archivos de encabezado precompilados, cuándo compilar"
  - "código fuente, precompilar"
ms.assetid: eb8ba193-fd87-40d3-9545-c75deabe37cb
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Cu&#225;ndo precompilar c&#243;digo fuente
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El código precompilado resulta útil durante el ciclo de desarrollo para reducir el tiempo de compilación, especialmente si:  
  
-   Se utiliza siempre un gran cuerpo de código que apenas cambia.  
  
-   El programa comprende varios módulos, los cuales utilizan un conjunto estándar de archivos de inclusión y las mismas opciones de compilación.  En este caso, todos los archivos de inclusión pueden precompilarse en un encabezado precompilado.  
  
 La primera compilación \(la que crea el archivo de encabezado precompilado\) dura algo más que las siguientes compilaciones.  Las compilaciones posteriores pueden efectuarse más rápidamente si se incluye el código precompilado.  
  
 Se pueden precompilar tanto programas en C como programas en C\+\+.  En la programación en C\+\+, es una práctica común separar la información de interfaz de las clases en archivos de encabezado.  Estos archivos de encabezado pueden incluirse posteriormente en programas que utilizan la clase.  Mediante la precompilación de estos encabezados, se puede reducir el tiempo de compilación de un programa.  
  
> [!NOTE]
>  Aunque sólo se puede utilizar un archivo de encabezado precompilado \(.pch\) por cada archivo de código fuente, es posible utilizar varios archivos .pch en un proyecto.  
  
## Vea también  
 [Crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md)