---
title: "/arch (x64) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: ecda22bf-5bed-43f4-99fb-88aedd83d9d8
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /arch (x64)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica la arquitectura para la generación de código en x64.  Vea también [\/arch \(x86\)](../../build/reference/arch-x86.md) y [\/arch \(ARM\)](../../build/reference/arch-arm.md).  
  
## Sintaxis  
  
```  
/arch:[AVX|AVX2]  
```  
  
## Argumentos  
 **\/arch:AVX**  
 Habilita el uso de instrucciones de Extensiones de vector avanzadas de Intel.  
  
 **\/arch:AVX2**  
 Habilita el uso de instrucciones de Extensiones de vector avanzadas 2 \(AVX2\) de Intel.  
  
## Comentarios  
 **\/arch** solo afecta a la generación de código de las funciones nativas.  Cuando se usa [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) para compilar, **\/arch** no tiene ningún efecto en la generación de código para las funciones administradas.  
  
 El símbolo de preprocesador `__AVX__` se define cuando se especifica opción del compilador **\/arch:AVX**.  El símbolo de preprocesador `__AVX2__` se define cuando se especifica opción del compilador **\/arch:AVX2**.  Para obtener más información, vea [Macros predefinidas](../../preprocessor/predefined-macros.md).  La opción **\/arch:AVX2** se introdujo en Visual Studio 2013 Update 2, versión 12.0.34567.1.  
  
### Para establecer la opción del compilador \/arch:AVX o \/arch:AVX2 en Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Elija la carpeta **Propiedades de configuración**, **C\/C\+\+**.  
  
3.  Seleccione la página de propiedades **Generación de código**.  
  
4.  En el cuadro desplegable **Habilitar conjunto de instrucciones mejorado**, elija **Extensiones de vector avanzadas \(\/arch:AVX\)** o **Extensiones de vector avanzadas 2 \(\/arch:AVX2\)**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Consulta <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.  
  
## Vea también  
 [\/arch \(Arquitectura de CPU mínima\)](../../build/reference/arch-minimum-cpu-architecture.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)