---
title: Cambiar un símbolo&#39;valor numérico s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.changing.value
dev_langs:
- C++
helpviewer_keywords:
- numeric values
- symbols, numeric values
- numeric values, changing symbols
ms.assetid: 468e903b-9c07-4251-ae09-3b6cb754cc2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 748b45b93f6145a03d8cd9745b7b61e3482ec53d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603749"
---
# <a name="changing-a-symbol39s-numeric-value"></a>Cambiar un símbolo&#39;valor numérico s

Para los símbolos asociados a un único recurso, puede usar el [ventana propiedades](/visualstudio/ide/reference/properties-window) para cambiar el valor de símbolo. Puede usar el [cuadro de diálogo símbolos de recursos](../windows/resource-symbols-dialog-box.md) para cambiar el valor de los símbolos no estén asignados a un recurso. Para obtener más información, consulte [cambiar símbolos sin asignar](../windows/changing-unassigned-symbols.md).

### <a name="to-change-a-symbol-value-assigned-to-a-single-resource-or-object"></a>Para cambiar el valor de un símbolo asignado a un solo recurso u objeto

1. En [vista de recursos](../windows/resource-view-window.md), seleccione el recurso.

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

2. En el **propiedades** ventana, escriba el nombre del símbolo seguido por un signo igual y un número entero en el **ID** cuadro, por ejemplo:

    ```
    IDC_EDITNAME=5100
    ```

El nuevo valor se almacena en el archivo de encabezado de símbolos la próxima vez que guarde el proyecto. En el cuadro Id. solo está visible el nombre del símbolo; el signo igual y el valor no se muestran después de su validación.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. . Para información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Restricciones de los valores de símbolo](../windows/symbol-value-restrictions.md)  
[Identificadores de símbolo predefinidos](../windows/predefined-symbol-ids.md)