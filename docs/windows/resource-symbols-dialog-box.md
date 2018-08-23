---
title: Cuadro de diálogo símbolos de recursos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.resourcesymbols
dev_langs:
- C++
helpviewer_keywords:
- New Symbol dialog box
- Resource Symbols dialog box
- Change Symbol dialog box
ms.assetid: 9706cde3-1f48-4fcd-bedb-2b03b455e3c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fc4c6a749a5e3ef1835d959e7803ac6b6f4435ec
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609824"
---
# <a name="resource-symbols-dialog-box"></a>Símbolos de recursos (cuadro de diálogo)

El **símbolos de recursos** cuadro de diálogo le permite agregar símbolos de recursos nuevos, cambiar los símbolos que se muestran o saltar a la ubicación en el código fuente en un símbolo está en uso.

**Name**  
Muestra el nombre del símbolo. Para obtener más información, consulte [restricciones de nombre de símbolo](../windows/symbol-name-restrictions.md).

**Valor**  
Muestra el valor numérico del símbolo. Para obtener más información, consulte [restricciones de valor de símbolo](../windows/symbol-value-restrictions.md).

**En uso**  
Si se selecciona, especifica si el símbolo se usa en uno o varios recursos. El o los recursos se enumeran en el cuadro Usado por.

**Mostrar símbolos de solo lectura**  
Si se selecciona, muestra los recursos de solo lectura. De forma predeterminada, el **símbolos de recursos** cuadro de diálogo muestra únicamente los recursos modificables en el archivo de script de recursos, pero con esta opción seleccionada, los recursos modificables aparecen en negrita y los recursos de solo lectura aparecen en texto sin formato.

**Utilizado por**  
Muestra el o los recursos que usan el símbolo seleccionado en la lista de símbolos. Para abrir el editor para un recurso determinado, seleccione el recurso en el **usado por** y haga clic en **Ver uso**. Para obtener más información, consulte [abrir el Editor de recursos para un símbolo determinado](../windows/opening-the-resource-editor-for-a-given-symbol.md).

**Nuevo**  
Se abre el **nuevo símbolo** cuadro de diálogo que le permite definir el nombre y, si es necesario, un valor para un nuevo identificador de recurso simbólico. Para obtener más información, consulte [crear nuevos símbolos](../windows/creating-new-symbols.md).

**Cambio**  
Se abre el **cambiar símbolo** cuadro de diálogo que le permite cambiar el nombre o valor de un símbolo. Si el símbolo es para un control o un recurso en uso, solo se puede cambiar desde el editor de recursos correspondiente. Para obtener más información, consulte [cambiar símbolos sin asignar](../windows/changing-unassigned-symbols.md).

**Ver uso**  
Abre el recurso que contiene el símbolo en el editor de recursos correspondiente. Para obtener más información, consulte [abrir el Editor de recursos para un símbolo determinado](../windows/opening-the-resource-editor-for-a-given-symbol.md).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Visualización de símbolos de recursos](../windows/viewing-resource-symbols.md)