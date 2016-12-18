---
title: "/Yl (Insertar referencia PCH para biblioteca de depuraci&#243;n) | Microsoft Docs"
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
  - "/yi"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Yl (opción del compilador) [C++]"
  - "Yl (opción del compilador) [C++]"
  - "-Yl (opción del compilador) [C++]"
ms.assetid: 8e4a396a-6790-4a9f-8387-df015a3220e7
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Yl (Insertar referencia PCH para biblioteca de depuraci&#243;n)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se utiliza cuando se crea una biblioteca de depuración que utiliza encabezados precompilados pero se produce un error de compilación.  
  
## Sintaxis  
  
```  
/Ylsymbol  
```  
  
```  
/Yl-  
```  
  
## Argumentos  
 `symbol`  
 Un símbolo arbitrario que se almacena en el módulo de objetos.  
  
 \-  
 Un signo menos \(\-\) que explícitamente deshabilita la opción del compilador **\/Yl** .  
  
## Comentarios  
 De forma predeterminada, el compilador utiliza la opción de **\/Yl** \(sin especificar *symbol*\).  La opción de **\/Yl** permite al depurador para obtener información completa sobre tipos.  **\/Yl\-** deshabilita el comportamiento predeterminado.  
  
 Cuando se compila un módulo con **\/Yc** y **\/Yl**`symbol`, el compilador crea un símbolo similar a \_\_@@\_PchSym\_@00@...@`symbol`, donde los puntos suspensivos \(...\) representan una cadena de caracteres generada por el vinculador, y lo almacena en el módulo de objetos.  Cualquier archivo de código fuente que se compile con este encabezado precompilado hace referencia al símbolo especificado, a causa de lo cual el vinculador incluye el módulo de objetos y su información de depuración desde la biblioteca.  
  
 Con esta opción, puede que se genere LNK1211.  Si se especifican las opciones [\/Yc \(Crear archivo de encabezado precompilado\)](../../build/reference/yc-create-precompiled-header-file.md) y [\/Z7, \/Zi, \/ZI \(Formato de la información de depuración\)](../../build/reference/z7-zi-zi-debug-information-format.md), el compilador crea un archivo de encabezado precompilado que contiene información de depuración.  Puede ocurrir un error si se almacena el encabezado precompilado en una biblioteca, ésta se utiliza para compilar un módulo de objetos y el código fuente no hace referencia a ninguna de las funciones que define el archivo de encabezado precompilado.  
  
 Para resolver el problema, especifique **\/Yl**`symbol`, donde `symbol` es el nombre de un símbolo arbitrario de la biblioteca, cuando cree un archivo de encabezado precompilado que no contiene ninguna definición de función.  Esta opción ordena al compilador que almacene la información de depuración en el archivo de encabezado precompilado.  
  
 Para obtener más información acerca de los encabezados precompilados, vea:  
  
-   [\/Y \(Encabezados precompilados\)](../../build/reference/y-precompiled-headers.md)  
  
-   [Crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md)  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)