---
title: "/doc (Procesar comentarios de documentaci&#243;n) (C/C++) | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles"
  - "/doc"
  - "VC.Project.VCCLCompilerTool.XMLDocumentationFileName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/doc (opción del compilador) [C++]"
  - "comentarios, código C++"
  - "-doc (opción del compilador) [C++]"
  - "documentación XML, comentarios de archivos de código fuente"
ms.assetid: b54f7e2c-f28f-4f46-9ed6-0db09be2cc63
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /doc (Procesar comentarios de documentaci&#243;n) (C/C++)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Provoca que el compilador procese comentarios de documentación en archivos de código fuente, y la creación de un archivo .xdc por cada archivo de código fuente que tenga comentarios de documentación.  
  
## Sintaxis  
  
```  
/doc[name]  
```  
  
## Argumentos  
 `name`  
 El nombre del archivo .xdc que creará el compilador.  Sólo es válido cuando se pasa un archivo .cpp en la compilación.  
  
## Comentarios  
 Los archivos .xdc se procesan en un archivo .xml con xdcmake.exe.  Para obtener más información, vea [XDCMake \(Referencia\)](../../ide/xdcmake-reference.md).  
  
 Puede agregar los comentarios de documentación a sus archivos de código fuente.  Para obtener más información, vea [Etiquetas recomendadas para comentarios de documentación](../../ide/recommended-tags-for-documentation-comments-visual-cpp.md).  
  
 **\/doc** no es compatible con **\/clr:oldSyntax**.  Vea [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md) para obtener más información.  
  
 Para utilizar el archivo .xml generado con IntelliSense, haga coincidir el nombre del archivo .xml con el del ensamblado que desea admitir y ponga el archivo .xml en el mismo directorio que el ensamblado.  Cuando se haga referencia al ensamblado en el proyecto de Visual Studio, también se encontrará el archivo .xml.  Para obtener más información, vea [Utilizar IntelliSense](../Topic/Using%20IntelliSense.md) y [Proporcionar comentarios del código XML](../Topic/Supplying%20XML%20Code%20Comments.md).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Expanda el nodo **Propiedades de configuración**.  
  
3.  Expanda el nodo **C\/C\+\+**.  
  
4.  Seleccione la página de propiedades **Archivos de resultados**.  
  
5.  Modifique la propiedad **Generar archivos de documentación XML**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GenerateXMLDocumentationFiles%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)