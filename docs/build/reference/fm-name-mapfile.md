---
title: "/Fm (Asignar nombre al archivo de asignaciones) | Microsoft Docs"
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
  - "/fm"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Fm (opción del compilador) [C++]"
  - "archivos [C++], crear mapa"
  - "Fm (opción del compilador) [C++]"
  - "-Fm (opción del compilador) [C++]"
  - "archivos de asignaciones [C++], crear vinculador"
ms.assetid: 8154448a-93a7-4546-8e4c-5c44d0aff45d
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Fm (Asignar nombre al archivo de asignaciones)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Indica al vinculador que genere un archivo de asignaciones que contiene una lista de segmentos en el orden en que aparecen en el archivo .exe o DLL correspondiente.  
  
## Sintaxis  
  
```  
/Fmpathname  
```  
  
## Comentarios  
 De forma predeterminada, el archivo de asignaciones recibe el nombre base del archivo de código fuente de C o C\+\+ correspondiente, con la extensión .MAP.  
  
 Si se especifica **\/Fm**, tiene el mismo efecto que si se hubiese especificado la opción del vinculador [\/MAP \(Generar archivo de asignaciones\)](../../build/reference/map-generate-mapfile.md).  
  
 Si especifica [\/c \(Compilar sin vincular\)](../../build/reference/c-compile-without-linking.md) para suprimir la vinculación, **\/Fm** no se aplica.  
  
 Los símbolos globales en un archivo de asignaciones normalmente llevan delante uno o varios caracteres de subrayado, porque el compilador agrega un carácter de subrayado inicial a los nombres de variable.  El compilador y las bibliotecas estándar utilizan internamente muchos de los símbolos globales que aparecen en el archivo de asignaciones.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [\/F \(Opciones del archivo de resultados\)](../../build/reference/output-file-f-options.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Especificar la ruta de acceso](../../build/reference/specifying-the-pathname.md)