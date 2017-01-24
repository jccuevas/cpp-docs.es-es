---
title: "/hotpatch (Crear una imagen a la que se puede aplicar una revisi&#243;n reciente) | Microsoft Docs"
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
  - "/hotpatch"
  - "VC.Project.VCCLCompilerTool.CreateHotpatchableImage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aplicar una revisión reciente"
  - "-hotpatch (opción del compilador) [C++]"
  - "/hotpatch (opción del compilador) [C++]"
  - "aplicación de revisiones recientes"
ms.assetid: aad539b6-c053-4c78-8682-853d98327798
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /hotpatch (Crear una imagen a la que se puede aplicar una revisi&#243;n reciente)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Prepara una imagen para aplicar una revisión activa.  
  
## Sintaxis  
  
```  
/hotpatch  
```  
  
## Comentarios  
 Cuando se utiliza **\/hotpatch** en una compilación, el compilador se asegura de que la primera instrucción de cada función sea al menos de dos bytes, ya que es necesario para la revisión activa.  
  
 Para completar la preparación de una imagen para que se le pueda aplicar la revisión activa, después de utilizar **\/hotpatch** para compilar, debe utilizar [\/FUNCTIONPADMIN \(Crear una imagen a la que se puede aplicar una revisión reciente\)](../../build/reference/functionpadmin-create-hotpatchable-image.md) para vincular.  Cuando compila y vincula una imagen mediante una invocación de cl.exe, **\/hotpatch** implica **\/functionpadmin**.  
  
 Puesto que las instrucciones siempre son de dos bytes o mayores en la arquitectura de ARM y dado que la compilación x64 siempre se trata como si se hubiera especificado **\/hotpatch**, no es necesario especificar **\/hotpatch** al compilar para estos destinos; sin embargo, aún debe vincular mediante **\/functionpadmin** para crear imágenes de ellos a las que se pueda aplicar la revisión activa.  La opción del compilador **\/hotpatch** afecta solo a la compilación de x86.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Seleccione la carpeta **C\/C\+\+**.  
  
3.  Seleccione la página de propiedades **Línea de comandos**.  
  
4.  Agregue la opción del compilador al cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Guía  
 Para obtener más información sobre la administración de actualizaciones, vea “Guía de seguridad para la administración de actualizaciones” en [http:\/\/www.microsoft.com\/technet\/security\/guidance\/PatchManagement.mspx](http://www.microsoft.com/technet/security/guidance/PatchManagement.mspx).  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)