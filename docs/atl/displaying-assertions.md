---
title: Mostrar aserciones | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- debugging [ATL], displaying assertions
- assertions, displaying
- debugging assertions
- assertions, debugging
ms.assetid: fa353fe8-4656-4384-a5d2-8866bc977f06
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bff1ab29841ff2dd9973d538bb763d1fc1126a8f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="displaying-assertions"></a>Mostrar aserciones
Si el cliente conectado a su servicio parece dejar de responder, el servicio puede se imponen y muestra un cuadro de mensaje que no pueda ver. Puede confirmarlo utilizando el depurador de Visual C++ para depurar el código (vea [utilizando el Administrador de tareas](../atl/using-task-manager.md) anteriormente en esta sección).  
  
 Si determina que el servicio está mostrando un cuadro de mensaje que no aparecen, puede que desee establecer el **permitir a los servicios que interactúen con el escritorio** opción antes de volver a utilizar el servicio. Esta opción es un parámetro de inicio que permite que los cuadros de mensaje mostrados por el servicio que aparezca en el escritorio. Para establecer esta opción, abra la aplicación de Panel de Control de servicios, seleccione el servicio, haga clic en **inicio**y, a continuación, seleccione la **permitir a los servicios que interactúen con el escritorio** opción.  
  
## <a name="see-also"></a>Vea también  
 [Sugerencias de depuración](../atl/debugging-tips.md)

