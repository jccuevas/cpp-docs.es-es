---
title: Filtrar Creación de símbolos (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.symbol.creating
- vc.editors.symbol.managing
- vc.editors.resourcesymbols
- vc.editors.symbol.resource
helpviewer_keywords:
- New Symbol dialog box [C++]
- symbols [C++], creating
- resources [C++], viewing
- resource symbols
- symbols [C++], viewing
- New Symbol dialog box [C++]
- Resource Symbols dialog box [C++]
- Change Symbol dialog box [C++]
- resource symbols
- View Use button
- resource editors [C++], resource symbols
ms.assetid: 35168d31-3af6-4ecd-9362-3707d47b53f3
ms.openlocfilehash: 7dda3dc04b055226a0ae9788e6a98f6261256e7f
ms.sourcegitcommit: f127b08f114b8d6cab6b684febcb6f2ae0e055ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/27/2019
ms.locfileid: "56954892"
---
# <a name="how-to-create-symbols-c"></a>Filtrar Creación de símbolos (C++)

Si está empezando un proyecto nuevo, le resultará conveniente asignar los nombres de símbolo que necesita antes de crear los recursos a los que podrán asignadas.

El **símbolos de recursos** cuadro de diálogo le permite agregar símbolos de recursos nuevos, cambiar los símbolos que se muestran o saltar a la ubicación en el código fuente en un símbolo está en uso.

El cuadro de diálogo contiene las siguientes propiedades:

|Property|Descripción|
|--------------------------|------------------------------------------|
|**Name**|Muestra el nombre del símbolo. Para obtener más información, consulte [restricciones de nombre de símbolo](../windows/symbol-name-restrictions.md).|
|**Valor**|Muestra el valor numérico del símbolo. Para obtener más información, consulte [restricciones de valor de símbolo](../windows/symbol-value-restrictions.md).|
|**En uso**|Si se selecciona, especifica si el símbolo se usa en uno o varios recursos. El o los recursos se enumeran en el cuadro Usado por.|
|**Mostrar símbolos de solo lectura**|Si se selecciona, muestra los recursos de solo lectura. De forma predeterminada, el **símbolos de recursos** cuadro de diálogo muestra únicamente los recursos modificables en el archivo de script de recursos, pero con esta opción seleccionada, los recursos modificables aparecen en negrita y los recursos de solo lectura aparecen en texto sin formato.|
|**Utilizado por**|Muestra el o los recursos que usan el símbolo seleccionado en la lista de símbolos. Para abrir el editor para un recurso determinado, seleccione el recurso en el **usado por** y elija **Ver uso**.|
|**Nuevo**|Se abre el **nuevo símbolo** cuadro de diálogo que le permite definir el nombre y, si es necesario, un valor para un nuevo identificador de recurso simbólico.|
|**Change**|Se abre el **cambiar símbolo** cuadro de diálogo que le permite cambiar el nombre o valor de un símbolo. Si el símbolo es para un control o un recurso en uso, solo se puede cambiar desde el editor de recursos correspondiente. Para obtener más información, consulte [administrar símbolos](../windows/changing-unassigned-symbols.md).|
|**Ver uso**|Abre el recurso que contiene el símbolo en el editor de recursos correspondiente.|

## <a name="create-symbols"></a>Creación de símbolos

Para crear un nuevo símbolo:

1. En el **símbolos de recursos** diálogo cuadro, elija **New**.

1. En el **nombre** , escriba un nombre de símbolo.

1. Acepte el valor de símbolo asignado o escriba un nuevo valor en el **valor** cuadro.

1. Seleccione **Aceptar** para agregar el nuevo símbolo a la lista de símbolos.

> [!NOTE]
> Si escribe un nombre de símbolo que ya existe, aparecerá un cuadro de mensaje que indica que ya está definido un símbolo con ese nombre. No se puede definir dos o más símbolos con el mismo nombre, pero puede definir símbolos diferentes con el mismo valor numérico.

Para ver símbolos de recursos:

1. En [vista de recursos](../windows/resource-view-window.md), haga clic en el archivo .rc.

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Cómo: Crear recursos](../windows/how-to-create-a-resource-script-file.md).

1. Seleccione **símbolos de recursos** en el menú contextual para ver una tabla de símbolos de recursos en el **símbolos de recursos** cuadro de diálogo.

   > [!NOTE]
   > Para ver los símbolos predefinidos, consulte el **mostrar símbolos de solo lectura** casilla de verificación.

Para abrir el editor de recursos para un símbolo determinado:

Cuando esté navegando símbolos en el **símbolos de recursos**, es posible que desee obtener más información sobre cómo se utiliza un símbolo concreto. El **Ver uso** botón proporciona una forma rápida de obtener esta información.

1. Seleccione un símbolo en el **nombre** cuadro de la **símbolos de recursos** cuadro de diálogo.

1. En el **usado por** , seleccione el tipo de recurso que le interese.

1. Seleccione el **Ver uso** botón.

   El recurso se abrirá en la ventana del editor correspondiente.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Identificadores de recursos (símbolos)](../windows/symbols-resource-identifiers.md)<br/>
[Cómo: Administrar símbolos](../windows/changing-a-symbol-or-symbol-name-id.md)<br/>
[Identificadores de símbolo predefinidos](../windows/predefined-symbol-ids.md)<br/>