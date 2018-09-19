---
title: Cuadro de diálogo (C++) de símbolos de recursos | Microsoft Docs
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
- New Symbol dialog box [C++]
- Resource Symbols dialog box [C++]
- Change Symbol dialog box [C++]
ms.assetid: 9706cde3-1f48-4fcd-bedb-2b03b455e3c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 09d34d0247f7fd039bca3ea9b643802856734926
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719308"
---
# <a name="resource-symbols-dialog-box-c"></a>Cuadro de diálogo símbolos de recursos (C++)

El **símbolos de recursos** cuadro de diálogo de C++ le permite agregar símbolos de recursos nuevos, cambiar los símbolos que se muestran o saltar a la ubicación en el código fuente en un símbolo está en uso.

- **Name**

   Muestra el nombre del símbolo. Para obtener más información, consulte [restricciones de nombre de símbolo](../windows/symbol-name-restrictions.md).

- **Valor**

   Muestra el valor numérico del símbolo. Para obtener más información, consulte [restricciones de valor de símbolo](../windows/symbol-value-restrictions.md).

- **En uso**

   Si se selecciona, especifica si el símbolo se usa en uno o varios recursos. El o los recursos se enumeran en el cuadro Usado por.

- **Mostrar símbolos de solo lectura**

   Si se selecciona, muestra los recursos de solo lectura. De forma predeterminada, el **símbolos de recursos** cuadro de diálogo muestra únicamente los recursos modificables en el archivo de script de recursos, pero con esta opción seleccionada, los recursos modificables aparecen en negrita y los recursos de solo lectura aparecen en texto sin formato.

- **Utilizado por**

   Muestra el o los recursos que usan el símbolo seleccionado en la lista de símbolos. Para abrir el editor para un recurso determinado, seleccione el recurso en el **usado por** y haga clic en **Ver uso**. Para obtener más información, consulte [abrir el Editor de recursos para un símbolo determinado](../windows/opening-the-resource-editor-for-a-given-symbol.md).

- **Nuevo**

   Se abre el **nuevo símbolo** cuadro de diálogo que le permite definir el nombre y, si es necesario, un valor para un nuevo identificador de recurso simbólico. Para obtener más información, consulte [crear nuevos símbolos](../windows/creating-new-symbols.md).

- **Cambio**

   Se abre el **cambiar símbolo** cuadro de diálogo que le permite cambiar el nombre o valor de un símbolo. Si el símbolo es para un control o un recurso en uso, solo se puede cambiar desde el editor de recursos correspondiente. Para obtener más información, consulte [cambiar símbolos sin asignar](../windows/changing-unassigned-symbols.md).

- **Ver uso**

   Abre el recurso que contiene el símbolo en el editor de recursos correspondiente. Para obtener más información, consulte [abrir el Editor de recursos para un símbolo determinado](../windows/opening-the-resource-editor-for-a-given-symbol.md).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Visualización de símbolos de recursos](../windows/viewing-resource-symbols.md)