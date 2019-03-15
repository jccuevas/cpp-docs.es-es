---
title: / CETCOMPAT (compatible con tecnología de cumplimiento de flujo de Control)
ms.date: 02/19/2019
f1_keywords:
- /CETCOMPAT
helpviewer_keywords:
- /CETCOMPAT linker option
- /CETCOMPAT
ms.openlocfilehash: 1a01dd45667f64dbcbe11acaf1180835bd0d6e31
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809852"
---
# <a name="cetcompat-control-flow-enforcement-technology-compatible"></a>/ CETCOMPAT (compatible con tecnología de cumplimiento de flujo de Control)

Especifica si se debe marcar una imagen ejecutable como compatible con la tecnología de cumplimiento de flujo de Control (CET).

## <a name="syntax"></a>Sintaxis

> **/CETCOMPAT**\[**:NO**]

## <a name="arguments"></a>Argumentos

**NO**<br/>
Especifica que el archivo ejecutable no se debe marcar compatible con CET.

## <a name="remarks"></a>Comentarios

Tecnología de cumplimiento de flujo de control (CET) es una característica de procesador del equipo que proporciona funcionalidades para defenderse contra ciertos tipos de ataques de malware. Para obtener más información, consulte [cumplimiento Technology Preview de flujo de Control de Intel](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf).

El **/CETCOMPAT** opción del vinculador indica al vinculador para marcar el archivo binario como CET compatible. **/CETCOMPAT:no** marca el archivo binario que no es compatible con CET. Si ambas opciones se especifican en la línea de comandos, se usa la última de ellas especificada. Actualmente, este modificador solo es aplicable a las arquitecturas x86 y x64.

El **/CETCOMPAT** opción está disponible a partir el conjunto de herramientas de Visual Studio 2019 Preview 3.

### <a name="to-set-the-cetcompat-linker-option-in-visual-studio"></a>Para establecer la opción del vinculador /CETCOMPAT en Visual Studio

1. Abra el **páginas de propiedades** cuadro de diálogo para el proyecto. Para obtener más información, vea [Trabajar con propiedades de proyecto](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **línea de comandos** página de propiedades.

1. En el **opciones adicionales** , agregue **/CETCOMPAT** o **/CETCOMPAT:NO** y, a continuación, elija **Aceptar** o **aplicar**para guardar los cambios.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

Esta opción no tiene un equivalente mediante programación.

## <a name="see-also"></a>Vea también

[Opciones del vinculador](linker-options.md)
