---
title: Crear nuevos símbolos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.creating
dev_langs:
- C++
helpviewer_keywords:
- New Symbol dialog box [C++]
- symbols [C++], creating
ms.assetid: 35168d31-3af6-4ecd-9362-3707d47b53f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 91d27752af42b861c0374e9d8881db9e121fd5fd
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315332"
---
# <a name="creating-new-symbols"></a>Crear nuevos símbolos

Cuando inicie un proyecto nuevo, le resultará conveniente asignar los nombres de símbolo que necesita antes de crear los recursos a los que se asignarán.

### <a name="to-create-a-new-symbol-using-the-resource-symbols-dialog-box"></a>Para crear un nuevo símbolo mediante el cuadro de diálogo Símbolos de recursos

1. En el [cuadro de diálogo símbolos de recursos](../windows/resource-symbols-dialog-box.md), elija **New**.

2. En el **nombre** , escriba un nombre de símbolo.

3. Acepte el valor de símbolo asignado.

   O bien

   En el **valor** , escriba un nuevo valor.

4. Haga clic en **Aceptar** para agregar el nuevo símbolo a la lista de símbolos.

Si escribe un nombre de símbolo que ya existe, aparecerá un cuadro de mensaje que indica que ya está definido un símbolo con ese nombre. No se pueden definir dos o más símbolos con el mismo nombre, pero es posible definir símbolos diferentes con el mismo valor numérico. Para obtener más información, consulte [restricciones de nombre de símbolo](../windows/symbol-name-restrictions.md) y [restricciones de valor de símbolo](../windows/symbol-value-restrictions.md).

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a recursos, mostrar recursos estáticos y asignar recursos de cadenas a las propiedades.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Visualización de símbolos de recursos](../windows/viewing-resource-symbols.md)  
[Identificadores de símbolo predefinidos](../windows/predefined-symbol-ids.md)