---
title: Mostrar aserciones
ms.date: 05/05/2019
helpviewer_keywords:
- debugging [ATL], displaying assertions
- assertions, displaying
- debugging assertions
- assertions, debugging
ms.assetid: fa353fe8-4656-4384-a5d2-8866bc977f06
ms.openlocfilehash: 962a33a7d5d922f7f1655e22b2c9d0acdcf8925c
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221266"
---
# <a name="displaying-assertions"></a>Mostrar aserciones

Si el cliente conectado a su servicio parece dejar de responder, el servicio puede tener impone y muestra un cuadro de mensaje que no se pueden ver. Puede confirmarlo con el depurador de Visual Studio para depurar el código (consulte [utilizando el Administrador de tareas](../atl/using-task-manager.md) anteriormente en esta sección).

Si determina que el servicio está mostrando un cuadro de mensaje que no puede ver, es posible que desea establecer el **permitir a los servicios en la interacción con el escritorio** opción antes de volver a usar el servicio. Esta opción es un parámetro de inicio que permite que los cuadros de mensaje mostrados por el servicio aparezca en el escritorio. Para establecer esta opción, abra la aplicación de Panel de Control de servicios, seleccione el servicio, haga clic en **inicio**y, a continuación, seleccione el **permitir a los servicios en la interacción con el escritorio** opción.

## <a name="see-also"></a>Vea también

[Sugerencias de depuración](../atl/debugging-tips.md)
