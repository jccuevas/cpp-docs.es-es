---
title: Ver símbolos de recursos (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.managing
- vc.editors.resourcesymbols
helpviewer_keywords:
- resources [C++], viewing
- resource symbols
- symbols [C++], viewing
- New Symbol dialog box [C++]
- Resource Symbols dialog box [C++]
- Change Symbol dialog box [C++]
ms.assetid: 4bcc06d9-7d36-486a-8a37-71da0541643c
ms.openlocfilehash: e61269261fc9172288f1edf58419009178c755d9
ms.sourcegitcommit: 63c072f5e941989636f5a2b13800b68bb7129931
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2019
ms.locfileid: "55763978"
---
# <a name="viewing-resource-symbols"></a>Ver símbolos de recursos

El **símbolos de recursos** cuadro de diálogo de C++ le permite agregar símbolos de recursos nuevos, cambiar los símbolos que se muestran o saltar a la ubicación en el código fuente en un símbolo está en uso.

El cuadro de diálogo contiene las siguientes propiedades:

|Property|Descripción|
|---|---|
|**Name**|Muestra el nombre del símbolo. Para obtener más información, consulte [restricciones de nombre de símbolo](../windows/symbol-name-restrictions.md).|
|**Valor**|Muestra el valor numérico del símbolo. Para obtener más información, consulte [restricciones de valor de símbolo](../windows/symbol-value-restrictions.md).|
|**En uso**|Si se selecciona, especifica si el símbolo se usa en uno o varios recursos. El o los recursos se enumeran en el cuadro Usado por.|
|**Mostrar símbolos de solo lectura**|Si se selecciona, muestra los recursos de solo lectura. De forma predeterminada, el **símbolos de recursos** cuadro de diálogo muestra únicamente los recursos modificables en el archivo de script de recursos, pero con esta opción seleccionada, los recursos modificables aparecen en negrita y los recursos de solo lectura aparecen en texto sin formato.|
|**Utilizado por**|Muestra el o los recursos que usan el símbolo seleccionado en la lista de símbolos. Para abrir el editor para un recurso determinado, seleccione el recurso en el **usado por** y haga clic en **Ver uso**. Para obtener más información, consulte [abrir el Editor de recursos para un símbolo determinado](../windows/opening-the-resource-editor-for-a-given-symbol.md).|
|**Nuevo**|Se abre el **nuevo símbolo** cuadro de diálogo que le permite definir el nombre y, si es necesario, un valor para un nuevo identificador de recurso simbólico. Para obtener más información, consulte [crear nuevos símbolos](../windows/creating-new-symbols.md).|
|**Change**|Se abre el **cambiar símbolo** cuadro de diálogo que le permite cambiar el nombre o valor de un símbolo. Si el símbolo es para un control o un recurso en uso, solo se puede cambiar desde el editor de recursos correspondiente. Para obtener más información, consulte [cambiar símbolos sin asignar](../windows/changing-unassigned-symbols.md).|
|**Ver uso**|Abre el recurso que contiene el símbolo en el editor de recursos correspondiente. Para obtener más información, consulte [abrir el Editor de recursos para un símbolo determinado](../windows/opening-the-resource-editor-for-a-given-symbol.md).|

## <a name="to-view-resource-symbols"></a>Para ver símbolos de recursos

1. En [vista de recursos](../windows/resource-view-window.md), haga clic en el archivo .rc.

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

1. Seleccione **símbolos de recursos** en el menú contextual para ver una tabla de símbolos de recursos en el **símbolos de recursos** cuadro de diálogo.

   > [!NOTE]
   > Para ver los símbolos predefinidos, consulte el **mostrar símbolos de solo lectura** casilla de verificación.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Símbolos: Identificadores de recursos](../windows/symbols-resource-identifiers.md)