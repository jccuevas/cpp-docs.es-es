---
title: /PROFILE (Generador de perfiles de Herramientas de rendimiento)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.Profile
helpviewer_keywords:
- -PROFILE linker option
- /PROFILE linker option
ms.assetid: e676baa1-5063-47a3-a357-ba0d1f0d1699
ms.openlocfilehash: ca68ae090c6e4e6e3e10f37ac0d225faee96746a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810008"
---
# <a name="profile-performance-tools-profiler"></a>/PROFILE (Generador de perfiles de Herramientas de rendimiento)

Produce un archivo de salida que se puede usar con el generador de perfiles de Herramientas de rendimiento.

## <a name="syntax"></a>Sintaxis

```
/PROFILE
```

## <a name="remarks"></a>Comentarios

/ PERFIL implica las siguientes opciones del vinculador:

- [/OPT:REF](opt-optimizations.md)

- / OPT: NOICF

- [/INCREMENTAL:NO](incremental-link-incrementally.md)

- [/FIXED:NO](fixed-fixed-base-address.md)

Y perfil hace que el vinculador generar una sección de reubicación en la imagen del programa.  Una sección de reubicación permite que el generador de perfiles transformar la imagen del programa para obtener datos de perfil.

**/ PERFIL** solo está disponible solo en las versiones Enterprise (desarrollo en equipo).  Para obtener más información sobre PREfast, vea [análisis de código para C/C ++ Overview](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Expanda el nodo **Propiedades de configuración**.

1. Expanda el **vinculador** nodo.

1. Seleccione el **avanzadas** página de propiedades.

1. Modificar el **perfil** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Profile%2A>.

## <a name="see-also"></a>Vea también

[Referencia MSVC del vinculador](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)
