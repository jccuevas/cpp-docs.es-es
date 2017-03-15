---
title: "/arch (ARM) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 4f1406ff-f174-487c-a126-8ab06cf447c1
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# /arch (ARM)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica la arquitectura para la generación de código en ARM.  Vea también [\/arch \(x86\)](../../build/reference/arch-x86.md) y [\/arch \(x64\)](../../build/reference/arch-x64.md).  
  
## Sintaxis  
  
```  
/arch:[ARMv7VE|VFPv4]  
```  
  
## Argumentos  
 **\/arch:ARMv7VE**  
 Permite el uso de instrucciones de extensiones de virtualización de ARMv7VE.  
  
 **\/arch:VFPv4**  
 Permite el uso de instrucciones VFPv4 de ARM.  Si no se especifica esta opción, VFPv3 es el valor predeterminado.  
  
## Comentarios  
 La macro `_M_ARM_FP` \(solo para ARM\) indica qué opción del compilador **\/arch** se utilizó, si se usó alguna.  Para obtener más información, vea [Macros predefinidas](../../preprocessor/predefined-macros.md).  
  
 Cuando se usa [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) para compilar, **\/arch** no tiene ningún efecto en la generación de código para las funciones administradas.  **\/arch** solo afecta a la generación de código de las funciones nativas.  
  
### Cómo establecer la opción del compilador \/arch:ARMv7VE o \/arch:VFPv4 en Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Seleccione la carpeta **C\/C\+\+**.  
  
3.  Seleccione la página de propiedades **Línea de comandos**.  
  
4.  En el cuadro **Opciones adicionales**, agregue `/arch:ARMv7VE` o `/arch:VFPv4`.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.  
  
## Vea también  
 [\/arch \(Arquitectura de CPU mínima\)](../../build/reference/arch-minimum-cpu-architecture.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)