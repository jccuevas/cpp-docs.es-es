---
title: /PGD (Especificar la base de datos para las optimizaciones guiadas por perfiles)
ms.date: 03/14/2018
f1_keywords:
- VC.Project.VCLinkerTool.ProfileGuidedDatabase
helpviewer_keywords:
- -PGD linker option
- /PGD linker option
ms.assetid: 9f312498-493b-461f-886f-92652257e443
ms.openlocfilehash: e1d7c9fcb94a9351ce94b66e04b4bfc523248f4e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319803"
---
# <a name="pgd-specify-database-for-profile-guided-optimizations"></a>/PGD (Especificar la base de datos para las optimizaciones guiadas por perfiles)

**La opción/PGD está en desuso.** A partir de Visual Studio 2015, prefiere la [/GENPROFILE o/fastgenprofile](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) opciones del vinculador en su lugar. Esta opción se utiliza para especificar el nombre del archivo .pgd utilizado por el proceso de optimización guiada por perfiles.

## <a name="syntax"></a>Sintaxis

> **/ PGD:**_nombre de archivo_

## <a name="argument"></a>Argumento

*filename*<br/>
Especifica el nombre del archivo .pgd que se usa para almacenar información sobre el programa en ejecución.

## <a name="remarks"></a>Comentarios

Cuando se usa el desuso [/LTCG: PGINSTRUMENT](ltcg-link-time-code-generation.md) opción, utilice **/PGD** para especificar un nombre no predeterminado o la ubicación del archivo PGD. Si no especifica **/PGD**, el nombre base del archivo PGD es el mismo que la salida (.exe o .dll) nombre base del archivo y se crea en el mismo directorio desde el que se invocó el vínculo.

Cuando se usa el desuso **/LTCG: PGOPTIMIZE** opción, utilice el **/PGD** opción para especificar el nombre del archivo .pgd a usar para crear la imagen optimizada. El *filename* argumento debe coincidir con el *filename* especificado para **/LTCG: PGINSTRUMENT**.

Para obtener más información, consulte [optimizaciones guiadas por perfiles](../profile-guided-optimizations.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **optimización** página de propiedades.

1. Modificar el **base de datos guiada por perfiles** propiedad. Elija **Aceptar** para guardar los cambios.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProfileGuidedDatabase%2A>.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)<br/>
