---
title: "/Og (optimizaciones globales) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.GlobalOptimizations"
  - "/og"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Og (opción del compilador) [C++]"
  - "asignación automática de registro"
  - "eliminación de subexpresiones comunes"
  - "optimizaciones globales (opción del compilador) [C++]"
  - "estructuras de bucle, optimizar"
  - "Og (opción del compilador) [C++]"
  - "-Og (opción del compilador) [C++]"
ms.assetid: d10630cc-b9cf-4e97-bde3-8d7ee79e9435
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# /Og (optimizaciones globales)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona optimizaciones locales y globales, asignación automática de registros y optimización de bucles.  Obsoleto.  
  
## Sintaxis  
  
```  
/Og  
```  
  
## Comentarios  
 Están disponibles las siguientes optimizaciones:  
  
-   Eliminación de subexpresiones comunes locales y globales  
  
     En esta optimización, el valor de una subexpresión común se calcula una sola vez.  En el ejemplo siguiente, si los valores de `b` y `c` no varían entre las tres expresiones, el compilador puede asignar el cálculo de `b + c` a una variable temporal y sustituirla por `b + c`:  
  
    ```  
    a = b + c;  
    d = b + c;  
    e = b + c;  
    ```  
  
     Para la optimización de subexpresiones comunes locales, el compilador examina la presencia de subexpresiones comunes en secciones breves del código.  Para la optimización de subexpresiones comunes globales, el compilador busca subexpresiones comunes en funciones completas.  
  
-   Asignación automática de registros  
  
     Esta optimización permite al compilador almacenar variables y subexpresiones de uso frecuente en registros; se omite la palabra clave `register`.  
  
-   Optimización de bucles  
  
     Esta optimización quita las subexpresiones invariables del cuerpo de un bucle.  Un bucle óptimo sólo contiene expresiones cuyos valores varían en cada ejecución del bucle.  En el ejemplo siguiente, la expresión `x + y` no varía en el cuerpo del bucle:  
  
    ```  
    i = -100;  
    while( i < 0 ) {  
        i += x + y;  
    }  
    ```  
  
     Tras la optimización,  `x + y`  se calcula una sola vez y no en cada ejecución del bucle:  
  
    ```  
    i = -100;  
    t = x + y;  
    while( i < 0 ) {  
        i += t;  
    }  
    ```  
  
     La optimización de bucles es mucho más eficaz cuando el compilador puede suponer que no existe efecto escalonado \(aliasing\), el cual se establece con [\_\_restrict](../../cpp/extension-restrict.md), [noalias](../../cpp/noalias.md) o [restrict](../../cpp/restrict.md).  
  
    > [!NOTE]
    >  Puede habilitar o deshabilitar la optimización global función por función mediante la directiva pragma `optimize`  con la opción `g`.  
  
 La opción **\/Og** también habilita la optimización del valor devuelto con nombre, que elimina el constructor y el destructor de copias de un valor devuelto basado en la pila.  Para obtener más información, vea [\/O1, \/O2 \(Minimizar tamaño, maximizar velocidad\)](../../build/reference/o1-o2-minimize-size-maximize-speed.md).  
  
 Para obtener información relacionada, vea [Generar funciones intrínsecas \(\/Oi\)](../../build/reference/oi-generate-intrinsic-functions.md) y [Optimización completa \(\/Ox\)](../../build/reference/ox-full-optimization.md).  
  
 **\/Og** está desusado; use [\/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md) u **\/O2**.  Para obtener más información, vea [Deprecated Compiler Options in Visual C\+\+ 2005](http://msdn.microsoft.com/es-es/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [\/O \(Opciones\) \(Optimizar código\)](../../build/reference/o-options-optimize-code.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)