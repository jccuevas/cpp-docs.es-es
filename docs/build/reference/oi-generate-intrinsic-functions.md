---
title: "/Oi (Generar funciones intr&#237;nsecas) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.EnableIntrinsicFunctions"
  - "/oi"
  - "VC.Project.VCCLWCECompilerTool.EnableIntrinsicFunctions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Oi (opción del compilador) [C++]"
  - "generar funciones intrínsecas (opción del compilado) [C++]"
  - "funciones intrínsecas, generar"
  - "Oi (opción del compilador) [C++]"
  - "-Oi (opción del compilador) [C++]"
ms.assetid: fa4a3bf6-0ed8-481b-91c0-add7636132b4
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /Oi (Generar funciones intr&#237;nsecas)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Reemplaza algunas llamadas a función con formas intrínsecas o especiales de la función, que aumentan la velocidad de ejecución de la aplicación.  
  
## Sintaxis  
  
```  
/Oi[-]  
```  
  
## Comentarios  
 Los programas que usan funciones intrínsecas son más rápidos porque carecen de la sobrecarga de las llamadas de función, pero pueden tener un mayor tamaño a causa del código adicional que se crea.  
  
 Vea [intrinsic](../../preprocessor/intrinsic.md) para obtener más información sobre las funciones que tienen formas intrínsecas.  
  
 **\/Oi** es sólo una solicitud al compilador para que reemplace algunas llamadas a función con formas intrínsecas; el compilador podría llamar a la función \(y no reemplazar la llamada a la función con una forma intrínseca\) si ello produjese una mejora del rendimiento.  
  
 **Específico de x86**  
  
 Las funciones de punto flotante intrínsecas no realizan comprobaciones especiales de los valores de entrada y, por lo tanto, operan sobre intervalos de entrada restringidos, y tienen condiciones de límite y control de excepciones diferentes que las rutinas de biblioteca del mismo nombre.  El uso de formas intrínsecas verdaderas implica la pérdida del control de excepciones IEEE, y la pérdida de la funcionalidad de `_matherr` y `errno`; lo último implica la pérdida de conformidad con ANSI.  No obstante, las formas intrínsecas pueden acelerar considerablemente los programas que hacen un uso intenso de las operaciones de punto flotante y, para muchos programas, los problemas de conformidad tienen poco valor práctico.  
  
 Puede usar la opción del compilador [Za](../../build/reference/za-ze-disable-language-extensions.md) para invalidar la generación de opciones de punto flotante de formas intrínsecas verdaderas.  En este caso, las funciones se generan como rutinas de biblioteca que pasan los argumentos directamente al chip de punto flotante, en lugar de insertarlos en la pila del programa.  
  
 **Específico de END x86**  
  
 También puede usar [intrinsic](../../preprocessor/intrinsic.md) para crear funciones intrínsecas o [función](../../preprocessor/function-c-cpp.md) para forzar explícitamente una llamada a función.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Optimización**.  
  
4.  Modifique la propiedad **Habilitar funciones intrínsecas**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableIntrinsicFunctions%2A>.  
  
## Vea también  
 [\/O \(Opciones\) \(Optimizar código\)](../../build/reference/o-options-optimize-code.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Intrínsecos del controlador](../../intrinsics/compiler-intrinsics.md)