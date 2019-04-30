---
title: /favor (optimizar para valores específicos de la arquitectura)
ms.date: 11/04/2016
f1_keywords:
- /favor
helpviewer_keywords:
- -favor compiler option [C++]
- /favor compiler option [C++]
ms.assetid: ad264df2-e30f-4d68-8bd0-10d6bee71a2a
ms.openlocfilehash: b914d3e6e7a2865ec610249ff51d320d7890adcb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292827"
---
# <a name="favor-optimize-for-architecture-specifics"></a>/favor (optimizar para valores específicos de la arquitectura)

**/ favor:** `option` genera el código que está optimizado para una arquitectura específica o para las características de microarquitecturas en arquitecturas el AMD y las arquitecturas de Intel.

## <a name="syntax"></a>Sintaxis

> **/ favor:**{**blend** | **ATOM** | **AMD64** | **INTEL64**}

## <a name="remarks"></a>Comentarios

**/favor:blend**<br/>
(x86 y x64) genera el código que está optimizado para las características de microarquitecturas en arquitecturas el AMD y las arquitecturas de Intel. Mientras **/favor: Blend** podría no ofrecer el mejor rendimiento posible en un procesador específico, se ha diseñado para ofrecer el mejor rendimiento en una amplia gama de procesadores x86 y x64. De forma predeterminada, **/favor: Blend** está en vigor.

**/favor:ATOM**<br/>
(x86 y x64) genera el código que está optimizado para las características del procesador Intel Atom y tecnología de procesador Intel Centrino Atom. Código que se genera mediante el uso de **/favor:ATOM** también puede generar instrucciones de Intel SSSE3, SSE3, SSE y SSE2 para los procesadores Intel.

**/favor:AMD64**<br/>
(sólo x64) optimiza el código generado para los procesadores Athlon que admiten las extensiones de 64 bits y AMD Opteron. El código optimizado puede ejecutar en x64 todas las plataformas compatibles. Código que se genera mediante el uso de **/favor:AMD64** podría provocar un rendimiento peor en procesadores de Intel que admiten Intel64.

**/favor:INTEL64**<br/>
(sólo x64) optimiza el código generado para los procesadores de Intel que admiten Intel64, lo que normalmente ofrece un mejor rendimiento para esa plataforma. El código resultante se puede ejecutar en cualquier x64 plataforma. Código que se genera con **/favor:INTEL64** podría provocar un rendimiento peor en AMD Opteron y Athlon procesadores que admiten las extensiones de 64 bits.

> [!NOTE]
> Arquitectura Intel64 se conocía anteriormente como Extended Memory 64 Technology, y la opción del compilador correspondiente era **/favor:EM64T**.

Para obtener información sobre cómo programar para la x64 arquitectura, consulte [x64 convenciones de Software](../x64-software-conventions.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **C o C++** carpeta.

1. Seleccione el **línea de comandos** página de propiedades.

1. Especifique la opción del compilador en el **opciones adicionales** cuadro.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
