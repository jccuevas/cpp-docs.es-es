---
title: "/GR (Habilitar la informaci&#243;n de tipo en tiempo de ejecuci&#243;n) | Microsoft Docs"
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
  - "/gr"
  - "VC.Project.VCCLWCECompilerTool.RuntimeTypeInfo"
  - "VC.Project.VCCLCompilerTool.RuntimeTypeInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Gr (opción del compilador) [C++]"
  - "habilitar la información de tipo en tiempo de ejecución (opción del compilador) [C++]"
  - "Gr (opción del compilador) [C++]"
  - "-Gr (opción del compilador) [C++]"
  - "RTTI (opción del compilador)"
ms.assetid: d1f9f850-dcec-49fd-96ef-e72d01148906
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /GR (Habilitar la informaci&#243;n de tipo en tiempo de ejecuci&#243;n)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Agrega código para comprobar tipos de objeto en tiempo de ejecución.  
  
## Sintaxis  
  
```  
/GR[-]  
```  
  
## Comentarios  
 Cuando **\/GR** está habilitada, el compilador define la macro de preprocesador `_CPPRTTI`.  La opción **\/GR** está activada de manera predeterminada.  **\/GR\-** deshabilita la información de tipo en tiempo de ejecución.  
  
 Utilice **\/GR** si el compilador no puede resolver estáticamente un tipo de objeto en su código.  Normalmente necesita la opción **\/GR** cuando su código utiliza [dynamic\_cast \(Operador\)](../../cpp/dynamic-cast-operator.md) o [typeid](../../cpp/typeid-operator.md).  Sin embargo, **\/GR** aumenta el tamaño de las secciones .rdata de su imagen.  Si su código no utiliza **dynamic\_cast** ni **typeid**, el uso de **\/GR\-** puede generar una imagen menor.  
  
 Para obtener más información acerca de la comprobación de tipos en tiempo de ejecución, vea [Información de tipos en tiempo de ejecución](../../cpp/run-time-type-information.md) en la *Referencia del lenguaje de C\+\+*.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Lenguaje**.  
  
4.  Modifique la propiedad **Habilitar información de tipo en tiempo de ejecución**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeTypeInfo%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)