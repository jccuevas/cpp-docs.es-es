---
title: "/Za, /Ze (Deshabilitar extensiones de lenguaje) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLWCECompilerTool.DisableLanguageExtensions"
  - "/za"
  - "/ze"
  - "VC.Project.VCCLCompilerTool.DisableLanguageExtensions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Za (opción del compilador) [C++]"
  - "/Ze (opción del compilador) [C++]"
  - "Deshabilitar extensiones de lenguaje (opción del compilador)"
  - "habilitar extensiones de lenguaje"
  - "extensiones de lenguaje"
  - "extensiones de lenguaje, deshabilitar en el compilador"
  - "Za (opción del compilador) [C++]"
  - "-Za (opción del compilador) [C++]"
  - "Ze (opción del compilador) [C++]"
  - "-Ze (opción del compilador) [C++]"
ms.assetid: 65e49258-7161-4289-a176-7c5c0656b1a2
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# /Za, /Ze (Deshabilitar extensiones de lenguaje)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La opción **\/Za** del compilador emite un error para las construcciones de lenguaje que no son compatibles con ANSI C o ANSI C\+\+.  La opción **\/Ze** del compilador, que es el valor predeterminado, habilita las extensiones de Microsoft.  
  
## Sintaxis  
  
```  
/Za  
/Ze  
```  
  
## Comentarios  
  
> [!NOTE]
>  La opción **\/Ze** está desusada.  Para obtener más información, vea [Deprecated Compiler Options in Visual C\+\+ 2005](http://msdn.microsoft.com/es-es/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce).  
  
 El compilador de [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] ofrece varias características aparte de las especificadas en los estándares ANSI C o ANSI C\+\+.  Dichas características se conocen colectivamente como extensiones de Microsoft para C y C\+\+.  Estas extensiones están disponibles cuando se especifica la opción **\/Ze**, y no lo están cuando se especifica la opción **\/Za**.  Para obtener más información, vea [Extensiones de Microsoft para C y C\+\+](../../build/reference/microsoft-extensions-to-c-and-cpp.md).  
  
 Deshabilite las extensiones de lenguaje si desea trasladar un programa a otros entornos.  El compilador trata las palabras clave extendidas como simples identificadores, deshabilita las demás extensiones de Microsoft y define automáticamente la macro predefinida `__STDC__` para los programas de C.  
  
 Otras opciones del compilador utilizadas con **\/Za** pueden afectar a cómo el compilador garantiza la compatibilidad con ANSI.  Por ejemplo, **\/Za** y [\/fp \(Especificar comportamiento de punto flotante\)](../../build/reference/fp-specify-floating-point-behavior.md) pueden dar como resultado un comportamiento inesperado.  
  
 Vea la opción [\/Zc](../../build/reference/zc-conformance.md) del compilador para saber cómo conseguir un comportamiento estándar con **\/Za**.  
  
 Para obtener más información sobre los problemas de compatibilidad con [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)], vea [Problemas de compatibilidad y conformidad en Visual C\+\+](../../misc/compatibility-and-compliance-issues-in-visual-cpp.md).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Lenguaje**.  
  
4.  Modifique la propiedad **Deshabilitar extensiones de lenguaje**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)