---
title: "/Fe (Asignar nombre a un archivo ejecutable) | Microsoft Docs"
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
  - "/fe"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Fe (opción del compilador) [C++]"
  - "archivos ejecutables, cambiar nombre"
  - "Fe (opción del compilador) [C++]"
  - "-Fe (opción del compilador) [C++]"
  - "cambiar el nombre de los archivos (opción del compilador) [C++]"
ms.assetid: 49f594fd-5e94-45fe-a1bf-7c9f2abb6437
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Fe (Asignar nombre a un archivo ejecutable)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica un nombre y un directorio para el archivo .exe o .dll creado por el compilador.  
  
## Sintaxis  
  
```  
/Fepathname  
```  
  
## Comentarios  
 Sin esta opción, el compilador asigna al archivo un nombre predeterminado, formado con el nombre base del primer archivo objeto o de código fuente especificado en la línea de comandos y la extensión .exe o .dll.  
  
 Si se especifica [\/c \(Compilar sin vincular\)](../../build/reference/c-compile-without-linking.md) para compilar sin vinculación, **\/Fe** no tendrá efecto alguno.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **General**.  
  
4.  Modifique la propiedad **Archivo de salida**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>.  
  
## Ejemplo  
 La línea de comandos siguiente compila y vincula todos los archivos de código fuente C del directorio actual.  El archivo ejecutable resultante se denomina PROCESS.exe y se crea en el directorio C:\\BIN.  
  
```  
CL /FeC:\BIN\PROCESS *.C  
```  
  
## Ejemplo  
 La línea de comandos siguiente crea un archivo ejecutable en `C:\BIN` con el mismo nombre base que el primer archivo de código fuente o de objeto:  
  
```  
CL /FeC:\BIN\ *.C  
```  
  
## Vea también  
 [\/F \(Opciones del archivo de resultados\)](../../build/reference/output-file-f-options.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Especificar la ruta de acceso](../../build/reference/specifying-the-pathname.md)