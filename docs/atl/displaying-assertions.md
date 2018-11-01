---
title: Mostrar aserciones
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [ATL], displaying assertions
- assertions, displaying
- debugging assertions
- assertions, debugging
ms.assetid: fa353fe8-4656-4384-a5d2-8866bc977f06
ms.openlocfilehash: e183f782d488c2e5b92f61cfd63627f056e1f588
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616479"
---
# <a name="displaying-assertions"></a>Mostrar aserciones

Si el cliente conectado a su servicio parece dejar de responder, el servicio puede tener impone y muestra un cuadro de mensaje que no se pueden ver. Puede confirmarlo con el depurador de Visual C++ para depurar el código (consulte [utilizando el Administrador de tareas](../atl/using-task-manager.md) anteriormente en esta sección).

Si determina que el servicio está mostrando un cuadro de mensaje que no puede ver, es posible que desea establecer el **permitir a los servicios en la interacción con el escritorio** opción antes de volver a usar el servicio. Esta opción es un parámetro de inicio que permite que los cuadros de mensaje mostrados por el servicio aparezca en el escritorio. Para establecer esta opción, abra la aplicación de Panel de Control de servicios, seleccione el servicio, haga clic en **inicio**y, a continuación, seleccione el **permitir a los servicios en la interacción con el escritorio** opción.

## <a name="see-also"></a>Vea también

[Sugerencias de depuración](../atl/debugging-tips.md)

