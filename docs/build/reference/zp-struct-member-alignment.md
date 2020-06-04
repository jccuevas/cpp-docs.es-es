---
title: /Zp (Alineación de miembros de estructura)
ms.date: 04/04/2019
f1_keywords:
- /zp
- VC.Project.VCCLCompilerTool.StructMemberAlignment
- VC.Project.VCCLWCECompilerTool.StructMemberAlignment
helpviewer_keywords:
- Struct Member Alignment compiler option
- Zp compiler option
- /Zp compiler option [C++]
- -Zp compiler option [C++]
ms.assetid: 5242f656-ed9b-48a3-bc73-cfcf3ed2520f
ms.openlocfilehash: d76cd93c7af4228bff8f73fa3bcbf40fa149b0be
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315916"
---
# <a name="zp-struct-member-alignment"></a>/Zp (Alineación de miembros de estructura)

Controla cómo se empaquetan los miembros de una estructura en memoria y especifica el mismo tipo de empaquetado para todas las estructuras de un módulo.

## <a name="syntax"></a>Sintaxis

> **/Zp**[**1**|**2**|**4**|**8**|**16**]

## <a name="remarks"></a>Comentarios

El **/Zp**_n_ opción indica al compilador dónde almacenar cada miembro de estructura. El compilador almacena los miembros después de la primera de ellas en un límite que es el menor del tamaño del tipo de miembro, o un *n*-límite de bytes.

Los valores de empaquetado disponibles se describen en la tabla siguiente:

|/Zp argumento|Efecto|
|-|-|
|1|Empaqueta las estructuras en límites de 1 byte. Igual que **/Zp**.|
|2|Empaqueta las estructuras en límites de 2 bytes.|
|4|Empaqueta las estructuras en límites de 4 bytes.|
|8|Empaqueta las estructuras en límites de 8 bytes (valor predeterminado para x86, ARM y ARM64).|
|16| Empaqueta las estructuras en límites de 16 bytes (valor predeterminado para x64).|

No use esta opción a menos que tenga requisitos específicos de alineación.

> [!WARNING]
> Encabezados de C++ en el SDK de Windows, establecer y suponen **/zp8** empaquetado internamente. Memoria pueden dañarse si la **/Zp** se cambia la configuración dentro de los encabezados del SDK de Windows. Los encabezados no se ven afectados por ninguna **/Zp** opción se establece en la línea de comandos.

También puede usar [pack](../../preprocessor/pack.md) empaquetado de estructura de control. Para obtener más información sobre la alineación, vea:

- [align](../../cpp/align-cpp.md)

- [__alignof (Operador)](../../cpp/alignof-operator.md)

- [__unaligned](../../cpp/unaligned.md)

- [/ALIGN (Alineación de sección)](align-section-alignment.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **generación de código** página de propiedades.

1. Modificar el **alineación de miembros de Struct** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StructMemberAlignment%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador MSVC](compiler-options.md) \
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
