---
title: "/volatile (interpretaci&#243;n de la palabra clave volatile) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/volatile:iso"
  - "/volatile:ms"
  - "/volatile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/volatile (opción del compilador)"
  - "/volatile (opción del compilador) [C++]"
  - "volatile (opción del compilador)"
  - "-volatile (opción del compilador)"
  - "volatile (opción del compilador) [C++]"
  - "-volatile (opción del compilador) [C++]"
ms.assetid: 9d08fcc6-5bda-44c8-8151-8d8d54f164b8
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# /volatile (interpretaci&#243;n de la palabra clave volatile)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica cómo la palabra clave [volatile](../../cpp/volatile-cpp.md) debe interpretarse.  
  
## Sintaxis  
  
```  
/volatile:{iso|ms}  
```  
  
## Argumentos  
 **\/volatile:iso**  
 Selecciona la semántica estricta de `volatile` definida por el lenguaje C\+\+ de la norma ISO estándar.  La adquisición o versión de semántica no se garantiza en accesos volátiles.  Si el compilador tiene como destino ARM, ésta es la interpretación predeterminada de `volatile`.  
  
 **\/volatile:ms**  
 Selecciona la semántica de Microsoft mejorada de `volatile`, que agrega garantías de ordenación de memoria más allá del lenguaje C\+\+ de la norma ISO estándar.  La adquisición o versión de semántica se garantiza en accesos volátiles.  Sin embargo, esta opción también hace que el compilador genere barreras de memoria de hardware, que podrían agregar una gran sobrecarga en la ARM y otras arquitecturas de ordenación de memoria débil.  Si el compilador tiene como destino cualquier plataforma excepto la ARM, ésta es la interpretación predeterminada de `volatile`.  
  
## Comentarios  
 Se recomienda encarecidamente utilizar **\/volatile:iso** junto con primitivos explícitos de sincronización y función intrínseca del compilador cuando se trabaje con la memoria compartida entre subprocesos.  Para obtener más información, vea [volatile](../../cpp/volatile-cpp.md).  
  
 Si importa código existente o cambia esta opción en medio de un proyecto, puede ser útil permitir que la advertencia [C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md) identifique las ubicaciones del código que se ven afectadas por la diferencia en la semántica.  
  
 No hay equivalente de `#pragma` para controlar esta opción.  
  
### Para establecer la opción del compilador \/volatile en Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Seleccione la carpeta **C\/C\+\+**.  
  
3.  Seleccione la página de propiedades **Línea de comandos**.  
  
4.  En el cuadro de **Opciones adicionales**, agregue `/volatile: ISO` o `/volatile: ms`.  
  
## Vea también  
 [volatile](../../cpp/volatile-cpp.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)