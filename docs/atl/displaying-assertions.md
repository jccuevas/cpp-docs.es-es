---
title: Mostrar aserciones
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [ATL], displaying assertions
- assertions, displaying
- debugging assertions
- assertions, debugging
ms.assetid: fa353fe8-4656-4384-a5d2-8866bc977f06
ms.openlocfilehash: bb06b8f124180ed566ecf2c761deb359444fb019
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289995"
---
# <a name="displaying-assertions"></a>Mostrar aserciones

Si el cliente conectado a su servicio parece dejar de responder, el servicio puede tener impone y muestra un cuadro de mensaje que no se pueden ver. Puede confirmarlo con el depurador de Visual C++ para depurar el código (consulte [utilizando el Administrador de tareas](../atl/using-task-manager.md) anteriormente en esta sección).

Si determina que el servicio está mostrando un cuadro de mensaje que no puede ver, es posible que desea establecer el **permitir a los servicios en la interacción con el escritorio** opción antes de volver a usar el servicio. Esta opción es un parámetro de inicio que permite que los cuadros de mensaje mostrados por el servicio aparezca en el escritorio. Para establecer esta opción, abra la aplicación de Panel de Control de servicios, seleccione el servicio, haga clic en **inicio**y, a continuación, seleccione el **permitir a los servicios en la interacción con el escritorio** opción.

## <a name="see-also"></a>Vea también

[Sugerencias de depuración](../atl/debugging-tips.md)
