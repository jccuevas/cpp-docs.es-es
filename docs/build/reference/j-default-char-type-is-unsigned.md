---
title: "/J (El tipo de car&#225;cter predeterminado no tiene signo) | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.DefaultCharIsUnsigned"
  - "VC.Project.VCCLWCECompilerTool.DefaultCharIsUnsigned"
  - "/j"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/J (opción del compilador) [C++]"
  - "char (tipo de datos)"
  - "el tipo de carácter predeterminado no tiene signo"
  - "predeterminados, char (tipo)"
  - "J (opción del compilador) [C++]"
  - "-J (opción del compilador) [C++]"
ms.assetid: 50973667-6638-491e-9c41-bff73acae19f
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /J (El tipo de car&#225;cter predeterminado no tiene signo)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cambia `char` predeterminado con tipo de `signed char` a `unsigned char`, y cero\- se extiende el tipo de `char` cuando se amplía a un tipo de `int` .  
  
## Sintaxis  
  
```  
/J  
```  
  
## Comentarios  
 Si un valor de `char` se declara explícitamente como `signed`, la opción de **\/J** no le afecta, y signo\- se extiende el valor cuando se amplía a un tipo de `int` .  
  
 La opción **\/J** define `_CHAR_UNSIGNED`, que se utiliza con `#ifndef` en el archivo LIMITS.h para definir el intervalo del tipo `char` predeterminado.  
  
 ANSI C y C\+\+ no requieren una implementación específica del tipo `char`.  Esta opción es útil cuando se trabaja con datos de caracteres que en algún momento se convertirán a un idioma distinto del inglés.  
  
> [!NOTE]
>  Si utiliza esta opción del compilador con y MFC, un error puede ser generado.  Aunque se puede deshabilitar este error definiendo `_ATL_ALLOW_CHAR_UNSIGNED`, esta solución alternativa no se admite y no siempre funcione.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Propiedades**.  
  
2.  En el cuadro de diálogo de **Páginas de propiedades** del proyecto, en el panel izquierdo bajo **Propiedades de configuración**, expanda **C\/C\+\+** y seleccione **Línea de comandos**.  
  
3.  En el panel **Opciones adicionales**, especifique la opción de compilador **\/J**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md)