---
title: Mostrar aserciones | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [ATL], displaying assertions
- assertions, displaying
- debugging assertions
- assertions, debugging
ms.assetid: fa353fe8-4656-4384-a5d2-8866bc977f06
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f9133d2fadfa4158eef9755fff7e0d2a62478966
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32354284"
---
# <a name="displaying-assertions"></a>Mostrar aserciones
Si el cliente conectado a su servicio parece dejar de responder, el servicio puede se imponen y muestra un cuadro de mensaje que no pueda ver. Puede confirmarlo utilizando el depurador de Visual C++ para depurar el código (vea [utilizando el Administrador de tareas](../atl/using-task-manager.md) anteriormente en esta sección).  
  
 Si determina que el servicio está mostrando un cuadro de mensaje que no aparecen, puede que desee establecer el **permitir a los servicios que interactúen con el escritorio** opción antes de volver a utilizar el servicio. Esta opción es un parámetro de inicio que permite que los cuadros de mensaje mostrados por el servicio que aparezca en el escritorio. Para establecer esta opción, abra la aplicación de Panel de Control de servicios, seleccione el servicio, haga clic en **inicio**y, a continuación, seleccione la **permitir a los servicios que interactúen con el escritorio** opción.  
  
## <a name="see-also"></a>Vea también  
 [Sugerencias de depuración](../atl/debugging-tips.md)

