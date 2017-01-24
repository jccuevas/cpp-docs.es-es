---
title: "/Gs (Controlar llamadas de comprobaci&#243;n de la pila) | Microsoft Docs"
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
  - "/GS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/GS (opción del compilador) [C++]"
  - "deshabilitar comprobaciones de la pila"
  - "GS (opción del compilador) [C++]"
  - "-GS (opción del compilador) [C++]"
  - "llamadas de comprobación de la pila"
  - "comprobaciones de la pila"
  - "pila, comprobaciones de la pila"
ms.assetid: 40daed7c-f942-4085-b872-01e12b37729e
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Gs (Controlar llamadas de comprobaci&#243;n de la pila)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Controla las comprobaciones de la pila.  
  
## Sintaxis  
  
```  
/Gs[size]  
```  
  
## Argumentos  
 `size`  
 \(Opcional\) Número de bytes que pueden ocupar las variables locales antes de que se inicie un sondeo de pila.  Especificar la opción **\/Gs** sin un argumento de `size` equivale a especificar **\/Gs0**.  
  
## Comentarios  
 Un sondeo de pila es una secuencia de código que el compilador inserta en cada llamada de función.  Cuando se inicia un sondeo de pila, se introduce en la memoria sin causar conflictos, en la cantidad de espacio necesaria para almacenar las variables locales de la función.  
  
 Si una función requiere más de `size` bytes de espacio de la pila para las variables locales, se activará su sondeo de pila.  De forma predeterminada, el compilador genera código que inicia un sondeo de pila cuando una función requiere más de una página de espacio de pila.  Equivale a una opción del compilador de **\/Gs4096** en las plataformas x86, [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] y ARM.  Este valor permite a una aplicación y al administrador de memoria de Windows aumentar la cantidad de memoria asignada dinámicamente a la pila del programa en tiempo de ejecución.  
  
> [!NOTE]
>  El valor predeterminado de **\/Gs4096** permite que la pila de aplicaciones para Windows del programa aumente correctamente en tiempo de ejecución.  Le recomendamos que no cambie el valor predeterminado, excepto si sabe exactamente por qué tiene que cambiarlo.  
  
 Algunos programas, como los controladores de dispositivos virtuales, no requieren este mecanismo predeterminado de aumento de la pila.  En esos casos, no es necesario usar sondeos de pila: puede impedir que el compilador los genere configurando `size` con un valor mayor que el que requerirán las funciones para el almacenamiento de variables locales.  No se permite ningún espacio entre **\/Gs** y `size`.  
  
 **\/Gs0** activa los sondeos de pila para cada llamada de función que requiera el almacenamiento de variables locales.  Esto puede afectar negativamente al rendimiento.  
  
 Puede activar y desactivar las comprobaciones de la pila mediante [check\_stack](../../preprocessor/check-stack.md).  **\/Gs** y la pragma `check_stack` no afectan a las rutinas de la biblioteca de C estándar: afectan solamente a las funciones que se compilan.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Seleccione la carpeta **C\/C\+\+**.  
  
3.  Seleccione la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)