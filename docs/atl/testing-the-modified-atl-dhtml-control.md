---
title: Probar el Control DHTML ATL modificado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTML controls, testing
- testing controls
- DHTML controls, testing
ms.assetid: 42316118-9433-410f-9d8a-0efcc1eff824
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b140788cd409aa5a11f93689e96fa40c1a167dfe
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="testing-the-modified-atl-dhtml-control"></a>Probar el Control DHTML ATL modificado
Pruebe el nuevo control para ver cómo funciona ahora.  
  
#### <a name="to-build-and-test-the-modified-control"></a>Para compilar y probar el control modificado  
  
1.  Recompile el proyecto y ábralo en Test Container. Vea [Probar propiedades y eventos con Test Container](../mfc/testing-properties-and-events-with-test-container.md) para obtener información sobre cómo obtener acceso a Test Container.  
  
     El tamaño del control para mostrar todos los botones que agregó.  
  
2.  Examine los dos botones que insertó alterando el código HTML. Cada botón posee la etiqueta identificada en [modificar el Control DHTML ATL](../atl/modifying-the-atl-dhtml-control.md): **actualizar** y **HelloHTML**.  
  
3.  Pruebe los dos nuevos botones para ver cómo funcionan.  
  
 Ahora, pruebe los métodos que no forman parte de la interfaz de usuario.  
  
1.  Resalte el control, por lo que se activa el borde.  
  
2.  En el **Control** menú, haga clic en **invocar métodos**.  
  
 Los métodos de la lista con la etiqueta **nombre del método** son los métodos que puede llamar el contenedor: `MethodInvoked` y `GoToURL`. Todos los demás métodos se controlan mediante la interfaz de usuario.  
  
1.  Seleccione un método para invocar y haga clic en `Invoke` para mostrar el cuadro de mensaje del método o vaya a www.microsoft.com.  
  
2.  En el **invocar métodos** cuadro de diálogo, haga clic en **cerrar**.  
  
 Para obtener más información sobre los distintos elementos y archivos que componen un control DHTML ATL, vea [identifica los elementos del proyecto de Control DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md).  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con controles DHTML](../atl/atl-support-for-dhtml-controls.md)

