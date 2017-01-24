---
title: "/FC (Ruta de acceso completa de archivo de c&#243;digo fuente en diagn&#243;sticos) | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.UseFullPaths"
  - "/FC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/FC (opción del compilador) [C++]"
  - "-FC (opción del compilador) [C++]"
ms.assetid: 1f11414e-cb42-421b-be68-9d369aab036b
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /FC (Ruta de acceso completa de archivo de c&#243;digo fuente en diagn&#243;sticos)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Hace que el compilador muestre la ruta de acceso completa de archivos de código fuente que se ha pasado al compilador en diagnósticos.  
  
## Sintaxis  
  
```  
/FC  
```  
  
## Comentarios  
 Observe el siguiente código de ejemplo:  
  
```  
// compiler_option_FC.cpp  
int main( ) {  
   int i   // C2143  
}  
```  
  
 Sin **\/FC**, el texto de diagnóstico tendría un aspecto similar al del siguiente texto de diagnóstico:  
  
-   compiler\_option\_FC.cpp\(5\) : error C2143: error de sintaxis : falta ';' antes de '}'  
  
 Con **\/FC**, el texto de diagnóstico tendría un aspecto similar al siguiente texto de diagnóstico:  
  
-   c:\\test\\compiler\_option\_FC.cpp\(5\) : error C2143: error de sintaxis : falta ';' antes de '}'  
  
 También es necesaria la opción **\/FC** si se desea ver la ruta de acceso completa de un nombre de archivo cuando se utiliza la macro \_\_FILE\_\_.  Vea [Macros predefinidas](../../preprocessor/predefined-macros.md) para obtener más información sobre \_\_FILE\_\_.  
  
 La opción **\/FC** es implícita en **\/ZI**.  Para obtener más información sobre **\/ZI**, vea [\/Z7, \/Zi, \/ZI \(Formato de la información de depuración\)](../../build/reference/z7-zi-zi-debug-information-format.md).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Expanda el nodo **Propiedades de configuración**.  
  
3.  Expanda el nodo **C\/C\+\+**.  
  
4.  Seleccione la página de propiedades **Avanzadas**.  
  
5.  Modifique la propiedad **Utilizar rutas de acceso completas**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UseFullPaths%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)