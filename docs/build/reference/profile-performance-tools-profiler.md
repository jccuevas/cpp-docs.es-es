---
title: /PROFILE (Generador de perfiles de Herramientas de rendimiento)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.Profile
helpviewer_keywords:
- -PROFILE linker option
- /PROFILE linker option
ms.assetid: e676baa1-5063-47a3-a357-ba0d1f0d1699
ms.openlocfilehash: cf07154c6b681e2ad30a85a62a0db996c3f3d911
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078319"
---
# <a name="profile-performance-tools-profiler"></a>/PROFILE (Generador de perfiles de Herramientas de rendimiento)

Produce un archivo de salida que se puede usar con el generador de perfiles de Herramientas de rendimiento.

## <a name="syntax"></a>Sintaxis

```
/PROFILE
```

## <a name="remarks"></a>Observaciones

/PROFILE implica las siguientes opciones del vinculador:

- [/OPT: REF](opt-optimizations.md)

- /OPT: NOICF

- [/INCREMENTAL: NO](incremental-link-incrementally.md)

- [/FIXED: NO](fixed-fixed-base-address.md)

/PROFILE hace que el vinculador genere una sección de reubicación en la imagen del programa.  Una sección de reubicación permite que el generador de perfiles transforme la imagen de programa para obtener datos de perfil.

**/Profile** solo está disponible en las versiones Enterprise (Team Development).  Para obtener más información sobre las PREfast, vea [análisis de códigoC++ para C/Overview](/cpp/code-quality/code-analysis-for-c-cpp-overview).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Expanda el nodo **Propiedades de configuración**.

1. Expanda el nodo **Enlazador**.

1. Seleccione la página de propiedades **Avanzadas**.

1. Modifique la propiedad de **perfil** .

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Profile%2A>.

### <a name="to-set-this-linker-option-within-visual-studio-cmake-project"></a>Para establecer esta opción del vinculador en el proyecto CMake de Visual Studio

El proyecto **CMake** no tiene **páginas de propiedades**, las opciones del enlazador se pueden establecer Modifing archivo CMakeLists. txt.

1. Abra archivo CMakeLists. txt en el directorio raíz del proyecto.

1. Agregue el código siguiente. Para obtener más información, consulte [referencias de CMake](https://cmake.org/cmake/help/v3.0/command/set_target_properties.html)

1. Recompile la solución.

```
SET_TARGET_PROPERTIES(${PROJECT_NAME} PROPERTIES LINK_FLAGS "/PROFILE")
```

## <a name="see-also"></a>Consulte también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
