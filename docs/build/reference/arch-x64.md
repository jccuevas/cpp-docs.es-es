---
title: -arch (x64) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: ecda22bf-5bed-43f4-99fb-88aedd83d9d8
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 27a453601988c22ed03ae9cb267480d88d6a1cc0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="arch-x64"></a>/arch (x64)
Especifica la arquitectura para la generación de código en x64. Consulte también [/arch (x86)](../../build/reference/arch-x86.md) y [/arch (ARM)](../../build/reference/arch-arm.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/arch:[AVX|AVX2]  
```  
  
## <a name="arguments"></a>Argumentos  
 **/ arch: AVX**  
 Habilita el uso de instrucciones de Extensiones de vector avanzadas de Intel.  
  
 **/arch:AVX2**  
 Habilita el uso de instrucciones de Extensiones de vector avanzadas 2 (AVX2) de Intel.  
  
## <a name="remarks"></a>Comentarios  
 **/ arch** solo afecta a la generación de código para las funciones nativas. Cuando usas [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) para compilar, **/arch** no tiene ningún efecto sobre la generación de código para las funciones administradas.  
  
 El `__AVX__` se define el símbolo de preprocesador cuando la **/arch: AVX** se especifica la opción del compilador. El `__AVX2__` se define el símbolo de preprocesador cuando la **/arch:AVX2** se especifica la opción del compilador. Para obtener más información, consulta [Predefined Macros](../../preprocessor/predefined-macros.md). El **/arch:AVX2** opción se introdujo en Visual Studio 2013 Update 2, versión 12.0.34567.1.  
  
### <a name="to-set-the-archavx-or-archavx2-compiler-option-in-visual-studio"></a>Para establecer la opción del compilador /arch:AVX o /arch:AVX2 en Visual Studio  
  
1.  Abra la **páginas de propiedades** cuadro de diálogo para el proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione el **propiedades de configuración**, **C/C++** carpeta.  
  
3.  Seleccione el **generación de código** página de propiedades.  
  
4.  En el **Habilitar conjunto de instrucciones mejorado** desplegable cuadro, elija **extensiones de Vector avanzadas (/ arch: AVX)** o **extensiones de Vector avanzadas 2 (/ arch: AVX2)**.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.  
  
## <a name="see-also"></a>Vea también  
 [/arch (arquitectura de CPU mínima)](../../build/reference/arch-minimum-cpu-architecture.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)