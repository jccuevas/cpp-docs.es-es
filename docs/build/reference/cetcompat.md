---
title: / CETCOMPAT (pila de sombra CET compatible)
ms.date: 02/19/2019
f1_keywords:
- /CETCOMPAT
helpviewer_keywords:
- /CETCOMPAT linker option
- /CETCOMPAT
ms.openlocfilehash: 0ed5d9d4f9f4f4dc5cd4fc19df4179e86e430187
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273253"
---
# <a name="cetcompat-cet-shadow-stack-compatible"></a>/ CETCOMPAT (pila de sombra CET compatible)

Especifica si se debe marcar una imagen ejecutable como compatible con la pila de sombra de la tecnología de cumplimiento (CET) de flujo de Control.

## <a name="syntax"></a>Sintaxis

> **/CETCOMPAT**\[**:NO**]

## <a name="arguments"></a>Argumentos

**NO**<br/>
Especifica que el archivo ejecutable no se debe marcar compatible con la pila de sombra CET.

## <a name="remarks"></a>Comentarios

Pila de sombra de la tecnología de cumplimiento (CET) de flujo de control es una característica de procesador del equipo que proporciona funcionalidades para defenderse de programación orientada a devuelto (superior) en función de los ataques de malware. Para obtener más información, consulte [cumplimiento Technology Preview de flujo de Control de Intel](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf).

El **/CETCOMPAT** opción del vinculador indica al vinculador para marcar el archivo binario como pila sombra CET compatible. **/CETCOMPAT:no** marca el archivo binario que no es compatible con la pila de sombra CET. Si ambas opciones se especifican en la línea de comandos, se usa la última de ellas especificada. Actualmente, este modificador solo es aplicable a las arquitecturas x86 y x64.

El **/CETCOMPAT** opción está disponible a partir el conjunto de herramientas de Visual Studio 2019 Preview 3.

### <a name="to-set-the-cetcompat-linker-option-in-visual-studio"></a>Para establecer la opción del vinculador /CETCOMPAT en Visual Studio

1. Abra el **páginas de propiedades** cuadro de diálogo para el proyecto. Para obtener más información, vea [Trabajar con propiedades de proyecto](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **línea de comandos** página de propiedades.

1. En el **opciones adicionales** , agregue **/CETCOMPAT** o **/CETCOMPAT:NO** y, a continuación, elija **Aceptar** o **aplicar**para guardar los cambios.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

Esta opción no tiene un equivalente mediante programación.

## <a name="see-also"></a>Vea también

[Opciones del vinculador](linker-options.md)
