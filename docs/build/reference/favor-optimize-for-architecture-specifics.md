---
title: "-favor (optimizar para específicos de la arquitectura) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /favor
dev_langs: C++
helpviewer_keywords:
- -favor compiler option [C++]
- /favor compiler option [C++]
ms.assetid: ad264df2-e30f-4d68-8bd0-10d6bee71a2a
caps.latest.revision: "31"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 58b57183d7976d024a8a9d960f1f56ab438abff9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="favor-optimize-for-architecture-specifics"></a>/favor (optimizar para valores específicos de la arquitectura)
**/favor:** `option` genera el código optimizado para una arquitectura específica o para las características de microarquitecturas en arquitecturas el AMD y las arquitecturas de Intel.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/favor:{blend | ATOM | AMD64 | INTEL64}  
```  
  
## <a name="remarks"></a>Comentarios  
 **/ favor: Blend**  
 (x86 y x64) genera el código que se optimiza para las características de microarquitecturas en arquitecturas el AMD y las arquitecturas de Intel. Mientras **/favor: Blend** podría no ofrecer el mejor rendimiento posible en un procesador específico, se ha diseñado para ofrecer el mejor rendimiento en una amplia gama de procesadores x86 y x64. De forma predeterminada, **/favor: Blend** está en vigor.  
  
 **/favor:Atom**  
 (x86 y x64) genera el código que se optimiza para las características del procesador Intel Atom y tecnología de procesador Intel Centrino Atom. Código que se genera mediante **/favor:ATOM** también se puede generar instrucciones de Intel SSSE3, SSE3, SSE2 y SSE para los procesadores Intel.  
  
 **/favor:AMD64**  
 (sólo x64) optimiza el código generado para los procesadores Athlon que admiten las extensiones de 64 bits y AMD Opteron. El código optimizado puede ejecutar en x64 todas las plataformas compatibles. Código que se genera mediante **/favor:AMD64** puede provocar un rendimiento peor en procesadores Intel que admiten Intel64.  
  
 **/favor:INTEL64**  
 (sólo x64) optimiza el código generado para los procesadores Intel que admiten Intel64, lo que normalmente presenta un mejor rendimiento para esa plataforma. El código resultante se puede ejecutar en cualquier x64 plataforma. Código que se genera con **/favor:INTEL64** puede provocar un rendimiento peor en AMD Opteron y Athlon procesadores que admiten las extensiones de 64 bits.  
  
> [!NOTE]
>  Arquitectura de Intel64 se conocía anteriormente como tecnología Em64t, y la opción del compilador correspondiente era **/favor:EM64T**.  
  
 Para obtener información sobre cómo programar para la [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] arquitectura, consulte [x64 convenciones de Software](../../build/x64-software-conventions.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione el **C/C++** carpeta.  
  
3.  Seleccione el **línea de comandos** página de propiedades.  
  
4.  Escriba la opción del compilador en el **opciones adicionales** cuadro.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)