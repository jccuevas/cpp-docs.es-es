---
title: 'Cómo: crear símbolos (C++)'
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
ms.openlocfilehash: 1c69e8878885acd80c285691fb0861a476af03ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160520"
---
# <a name="how-to-create-symbols-c"></a>Cómo: crear símbolos (C++)

Al comenzar un proyecto nuevo, puede que le resulte conveniente asignar los nombres de símbolo que necesita antes de crear los recursos a los que se asignarán.

> [!NOTE]
> Si el proyecto aún no contiene un archivo. rc, consulte [Cómo: crear recursos](../windows/how-to-create-a-resource-script-file.md).

El cuadro de diálogo **símbolos de recursos** permite agregar nuevos símbolos de recursos, cambiar los símbolos que se muestran o saltar a la ubicación del código fuente donde se usa un símbolo.

El cuadro de diálogo contiene las siguientes propiedades:

|Propiedad|Descripción|
|--------------------------|------------------------------------------|
|**Nombre**|Muestra el nombre del símbolo.<br/><br/>Para obtener más información, vea [restricciones de nombre de símbolo](../windows/symbol-name-restrictions.md).|
|**Valor**|Muestra el valor numérico del símbolo.<br/><br/>Para obtener más información, vea [restricciones de valores de símbolo](../windows/symbol-value-restrictions.md).|
|**En uso**|Si se selecciona, especifica si el símbolo se usa en uno o varios recursos.<br/><br/>El recurso o los recursos se muestran en el cuadro **usado por** .|
|**Mostrar símbolos de solo lectura**|Si se selecciona, muestra los recursos de solo lectura.<br/><br/>De forma predeterminada, el cuadro de diálogo **símbolo de recurso** muestra solo los recursos modificables en el archivo de script de recursos, pero con esta opción seleccionada, los recursos modificables aparecen en negrita y los recursos de solo lectura aparecen en texto sin formato.|
|**Usado por**|Muestra el o los recursos que usan el símbolo seleccionado en la lista de símbolos.<br/><br/>Para ir al editor de un recurso determinado, seleccione el recurso en el cuadro **usado por** y elija **ver uso**.|
|**Nuevo**|Abre el cuadro de diálogo **nuevo símbolo** , que permite definir el nombre y, si es necesario, un valor para un nuevo identificador de recurso simbólico.|
|**Cambio**|Abre el cuadro de diálogo **cambiar símbolo** , que permite cambiar el nombre o el valor de un símbolo.<br/><br/>Si el símbolo es para un control o un recurso en uso, solo se puede cambiar desde el editor de recursos correspondiente. Para obtener más información, vea [administrar símbolos](../windows/changing-unassigned-symbols.md).|
|**Ver uso**|Abre el recurso que contiene el símbolo en el editor de recursos correspondiente.|

## <a name="create-symbols"></a>Crear símbolos

### <a name="to-create-a-new-symbol"></a>Para crear un nuevo símbolo

1. En el cuadro de diálogo **símbolos de recursos** , elija **nuevo**.

1. En el cuadro **nombre** , escriba un nombre de símbolo.

1. Acepte el valor de símbolo asignado o escriba un nuevo valor en el cuadro **valor** .

1. Seleccione **Aceptar** para agregar el nuevo símbolo a la lista de símbolos.

> [!NOTE]
> Si escribe un nombre de símbolo que ya existe, aparecerá un cuadro de mensaje que indica que ya está definido un símbolo con ese nombre. No se pueden definir dos o más símbolos con el mismo nombre, pero se pueden definir símbolos diferentes con el mismo valor numérico.

## <a name="to-view-resource-symbols"></a>Para ver símbolos de recursos

En [vista de recursos](how-to-create-a-resource-script-file.md#create-resources), haga clic con el botón secundario en el archivo *. RC* y seleccione **símbolos de recursos** para ver una tabla de símbolos de recursos en el cuadro de diálogo **símbolos de recursos** .

> [!NOTE]
> Para ver los símbolos predefinidos, active la casilla **Mostrar símbolos de solo lectura** .

### <a name="to-open-the-resource-editor-for-a-given-symbol"></a>Para abrir el editor de recursos para un símbolo determinado

Cuando examine símbolos en los **símbolos de recursos**, puede que desee obtener más información sobre cómo se usa un símbolo determinado. El botón **ver uso** proporciona una forma rápida de obtener esta información.

1. En el cuadro de diálogo **símbolos de recursos** , en el cuadro **nombre** , seleccione un símbolo.

1. En el cuadro **usado por** , seleccione el tipo de recurso que le interese.

1. Seleccione el botón **ver uso** .

   El recurso se abrirá en la ventana del editor correspondiente.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Consulte también

[Identificadores de recursos (símbolos)](../windows/symbols-resource-identifiers.md)<br/>
[Cómo: administrar símbolos](../windows/changing-a-symbol-or-symbol-name-id.md)<br/>
[Identificadores de símbolo predefinidos](../windows/predefined-symbol-ids.md)<br/>
