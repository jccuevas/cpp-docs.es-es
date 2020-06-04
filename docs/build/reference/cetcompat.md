---
title: /CETCOMPAT (compatibilidad con la pila de sombra de CET)
ms.date: 02/19/2019
f1_keywords:
- /CETCOMPAT
helpviewer_keywords:
- /CETCOMPAT linker option
- /CETCOMPAT
ms.openlocfilehash: 2c807d91d69b967fd62e01a077711dede5f55c44
ms.sourcegitcommit: 7e011c68ca7547469544fac87001a33a37e1792e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2020
ms.locfileid: "84421307"
---
# <a name="cetcompat-cet-shadow-stack-compatible"></a>/CETCOMPAT (compatibilidad con la pila de sombra de CET)

Especifica si se debe marcar una imagen ejecutable como compatible con la pila de sombras de la tecnología de aplicación de flujo de control (CET).

## <a name="syntax"></a>Sintaxis

> **/CETCOMPAT** \[ **: No**]

## <a name="arguments"></a>Argumentos

**No**<br/>
Especifica que el ejecutable no debe marcarse como compatible con la pila de sombra de CET.

## <a name="remarks"></a>Observaciones

La pila de instantáneas de la tecnología de aplicación de flujo de control (CET) es una característica de procesador del equipo que proporciona capacidades para defenderse frente a ataques de malware basados en la programación orientada a la devolución (ROP). Para obtener más información, consulte [versión preliminar de la tecnología de aplicación de flujo de control Intel](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf).

La opción del vinculador **/CETCOMPAT** indica al enlazador que marque el binario como compatible con la pila de sombra de CET. **/CETCOMPAT: no** marca el binario como no compatible con la pila de sombra de CET. Si se especifican ambas opciones en la línea de comandos, se usa la última especificada. Este modificador solo se aplica actualmente a las arquitecturas x86 y x64.

La opción **/CETCOMPAT** está disponible a partir del conjunto de herramientas de Visual Studio 2019 Preview 3.

### <a name="to-set-the-cetcompat-linker-option-in-visual-studio"></a>Para establecer la opción del vinculador/CETCOMPAT en Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades de proyecto](../working-with-project-properties.md).

1. Seleccione la **Configuration Properties**página de propiedades avanzadas del  >  **enlazador**de propiedades de configuración  >  **Advanced** .

1. Seleccione la propiedad **compatible con la pila de sombra de CET** .

1. En el control desplegable, elija **sí (/CETCOMPAT)** para habilitar los metadatos de continuación EH o **no (/CETCOMPAT: no)** para deshabilitarlo.


### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

Esta opción no tiene un equivalente de programación.

## <a name="see-also"></a>Consulte también

[Opciones del vinculador](linker-options.md)
