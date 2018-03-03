---
title: -arch (ARM) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 4f1406ff-f174-487c-a126-8ab06cf447c1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 468401bcee2d627149175d022c420b8bb905c4ed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="arch-arm"></a>/arch (ARM)
Especifica la arquitectura para la generación de código en ARM. Vea también [/arch (x86)](../../build/reference/arch-x86.md) y [/arch (x64)](../../build/reference/arch-x64.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/arch:[ARMv7VE|VFPv4]  
```  
  
## <a name="arguments"></a>Argumentos  
 **armv7ve**  
 Permite el uso de instrucciones de extensiones de virtualización de ARMv7VE.  
  
 **vfpv4**  
 Permite el uso de instrucciones VFPv4 de ARM. Si no se especifica esta opción, VFPv3 es el valor predeterminado.  
  
## <a name="remarks"></a>Comentarios  
 El `_M_ARM_FP` macro (solo para ARM) indica que, si existe, **/arch** se utilizó la opción del compilador. Para obtener más información, consulta [Predefined Macros](../../preprocessor/predefined-macros.md).  
  
 Cuando usas [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) para compilar, **/arch** no tiene ningún efecto sobre la generación de código para las funciones administradas. **/ arch** solo afecta a la generación de código para las funciones nativas.  
  
### <a name="to-set-the-archarmv7ve-or-archvfpv4-compiler-option-in-visual-studio"></a>Cómo establecer la opción del compilador /arch:ARMv7VE o /arch:VFPv4 en Visual Studio  
  
1.  Abra la **páginas de propiedades** cuadro de diálogo para el proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione el **C/C++** carpeta.  
  
3.  Seleccione el **línea de comandos** página de propiedades.  
  
4.  En el **opciones adicionales** , agregue `/arch:ARMv7VE` o `/arch:VFPv4`.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.  
  
## <a name="see-also"></a>Vea también  
 [/arch (arquitectura de CPU mínima)](../../build/reference/arch-minimum-cpu-architecture.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)