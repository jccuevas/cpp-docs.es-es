---
title: /PGD (Especificar la base de datos para las optimizaciones guiadas por perfiles)
ms.date: 03/14/2018
f1_keywords:
- VC.Project.VCLinkerTool.ProfileGuidedDatabase
helpviewer_keywords:
- -PGD linker option
- /PGD linker option
ms.assetid: 9f312498-493b-461f-886f-92652257e443
ms.openlocfilehash: 68d112c0a40289ba62e3fe5c37ae23f8f55f9209
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601297"
---
# <a name="pgd-specify-database-for-profile-guided-optimizations"></a>/PGD (Especificar la base de datos para las optimizaciones guiadas por perfiles)

**La opción/PGD está en desuso.** A partir de Visual Studio 2015, prefiere la [/GENPROFILE o/fastgenprofile](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) opciones del vinculador en su lugar. Esta opción se utiliza para especificar el nombre del archivo .pgd utilizado por el proceso de optimización guiada por perfiles.

## <a name="syntax"></a>Sintaxis

> **/ PGD:**_nombre de archivo_

## <a name="argument"></a>Argumento

*filename*<br/>
Especifica el nombre del archivo .pgd que se usa para almacenar información sobre el programa en ejecución.

## <a name="remarks"></a>Comentarios

Cuando se usa el desuso [/LTCG: PGINSTRUMENT](../../build/reference/ltcg-link-time-code-generation.md) opción, utilice **/PGD** para especificar un nombre no predeterminado o la ubicación del archivo PGD. Si no especifica **/PGD**, el nombre base del archivo PGD es el mismo que la salida (.exe o .dll) nombre base del archivo y se crea en el mismo directorio desde el que se invocó el vínculo.

Cuando se usa el desuso **/LTCG: PGOPTIMIZE** opción, utilice el **/PGD** opción para especificar el nombre del archivo .pgd a usar para crear la imagen optimizada. El *filename* argumento debe coincidir con el *filename* especificado para **/LTCG: PGINSTRUMENT**.

Para obtener más información, consulte [optimización guiada por perfiles](../../build/reference/profile-guided-optimizations.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **optimización** página de propiedades.

1. Modificar el **base de datos guiada por perfiles** propiedad. Elija **Aceptar** para guardar los cambios.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProfileGuidedDatabase%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)<br/>
