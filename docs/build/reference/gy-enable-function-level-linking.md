---
title: "/Gy (Habilitar vinculaci&#243;n en el nivel de funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.EnableFunctionLevelLinking"
  - "/gy"
  - "VC.Project.VCCLWCECompilerTool.EnableFunctionLevelLinking"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Gy (opción del compilador) [C++]"
  - "COMDAT (función)"
  - "habilitar vinculación en el nivel de función (opción del compilador) [C++]"
  - "Gy (opción del compilador) [C++]"
  - "-Gy (opción del compilador) [C++]"
  - "funciones empaquetadas"
ms.assetid: 0d3cf14c-ed7d-4ad3-b4b6-104e56f61046
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# /Gy (Habilitar vinculaci&#243;n en el nivel de funci&#243;n)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Permite que el compilador empaquete las funciones individuales con formato de funciones empaquetadas \(COMDATs\).  
  
## Sintaxis  
  
```  
/Gy[-]  
```  
  
## Comentarios  
 El vinculador requiere que las funciones se empaqueten de forma independiente como COMDAT para excluir u ordenar funciones individuales en un archivo DLL o .exe.  
  
 Utilice la opción del vinculador [\/OPT \(Optimizaciones\)](../../build/reference/opt-optimizations.md) para excluir del archivo .exe las funciones empaquetadas sin referencias.  
  
 Puede utilizar la opción del vinculador [\/ORDER \(Colocar las funciones en orden\)](../../build/reference/order-put-functions-in-order.md) para incluir las funciones empaquetadas en un orden concreto en el archivo .exe.  
  
 Las funciones inline siempre se empaquetan si sus instancias se crean como llamadas \(lo que ocurre, por ejemplo, si los procesos inline están desactivados o si se toma una dirección de función\).  Asimismo, las funciones miembro de C\+\+ definidas en la declaración de la clase se empaquetan de manera automática; esto no ocurre con otras funciones, y se requiere seleccionar esta opción para compilarlas como funciones empaquetadas.  
  
> [!NOTE]
>  La opción [\/ZI](../../build/reference/z7-zi-zi-debug-information-format.md), que se utiliza para Editar y continuar, establece la opción **\/Gy** de forma automática.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Generación de código**.  
  
4.  Modifique la propiedad **Habilitar vinculación en el nivel de función**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)