---
title: Probar el Control DHTML ATL | Documentos de Microsoft
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
- DHTML controls
- DHTML controls, testing
ms.assetid: 0e4b4358-80ce-4505-8b06-ef4f30b1d1f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2b523b981a58f577a3e98925899b32c0e9e69e98
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361871"
---
# <a name="testing-the-atl-dhtml-control"></a>Probar el Control DHTML ATL
Una vez haya creado el proyecto, puede crear y probar el control de ejemplo. Antes de hacerlo, use la vista de clases y Explorador de soluciones para examinar el proyecto. Los elementos del proyecto se describen con más detalle en [identifica los elementos del proyecto de Control DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md).  
  
#### <a name="to-build-and-test-the-atl-dhtml-control"></a>Para compilar y probar el control DHTML ATL  
  
1.  Compile el proyecto. Desde el **generar** menú, haga clic en **generar solución**.  
  
2.  Cuando se completa la compilación, abra el contenedor de prueba. Vea [Probar propiedades y eventos con Test Container](../mfc/testing-properties-and-events-with-test-container.md) para obtener información sobre cómo obtener acceso a Test Container.  
  
3.  En el contenedor de prueba, de la **editar** menú, haga clic en **Insertar nuevo Control**.  
  
4.  En el **insertar Control** cuadro de diálogo, seleccione el control del cuadro de lista. Recuerde que su nombre se basa en el nombre corto que especificó en el Asistente para controles ATL. Haga clic en **Aceptar**.  
  
5.  Examine el control. Tenga en cuenta que tiene una barra de desplazamiento. Use los controladores para cambiar el tamaño del control para activar la barra de desplazamiento.  
  
6.  Pruebe los botones del control. Cambia el color de fondo para el color indicado por el botón.  
  
7.  Cierre Test Container.  
  
 A continuación, intente [modificar el control DHTML](../atl/modifying-the-atl-dhtml-control.md).  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con controles DHTML](../atl/atl-support-for-dhtml-controls.md)

