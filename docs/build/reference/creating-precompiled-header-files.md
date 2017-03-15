---
title: "Crear archivos de encabezado precompilados | Microsoft Docs"
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
  - ".pch (archivos), crear"
  - "cl.exe (compilador), precompilar código"
  - "PCH (archivos), crear"
  - "archivos de encabezado precompilados, crear"
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Crear archivos de encabezado precompilados
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Los compiladores de Microsoft C y C\+\+ proporcionan opciones para precompilar cualquier código de C o C\+\+, incluido el código en línea.  Si se utiliza esta característica, es posible compilar un cuerpo estable de código, almacenar el código compilado en un archivo y, en sucesivas compilaciones, combinar el código precompilado con código aún en desarrollo.  Las compilaciones subsiguientes serán más rápidas, ya que no será necesario volver a compilar el código estable.  
  
 Esta sección trata los siguientes aspectos de encabezados precompilados:  
  
-   [Cuándo precompilar código fuente](../../build/reference/when-to-precompile-source-code.md)  
  
-   [Dos opciones para precompilar código](../../build/reference/two-choices-for-precompiling-code.md)  
  
-   [Reglas de coherencia de los encabezados precompilados](../../build/reference/precompiled-header-consistency-rules.md)  
  
-   [Utilizar encabezados precompilados en un proyecto](../../build/reference/using-precompiled-headers-in-a-project.md)  
  
 Para obtener información de referencia sobre las opciones del compilador relacionadas con encabezados precompilados, vea [\/Y \(encabezados precompilados\)](../../build/reference/y-precompiled-headers.md).  
  
## Vea también  
 [Referencia de compilación de C\/C\+\+](../../build/reference/c-cpp-building-reference.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)