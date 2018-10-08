---
title: Probar el Control DHTML ATL | Microsoft Docs
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
ms.openlocfilehash: ea2301a85411cea8d5ffd6121f4fb4f45d3196eb
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860854"
---
# <a name="testing-the-atl-dhtml-control"></a>Probar el Control DHTML ATL

Una vez que haya creado el proyecto, puede compilar y probar el control de ejemplo. Antes de hacerlo, use **vista de clases** y **el Explorador de soluciones** para examinar el proyecto. Los elementos del proyecto se describen con más detalle en [que identifican los elementos del proyecto de Control DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md).

## <a name="to-build-and-test-the-atl-dhtml-control"></a>Para compilar y probar el control DHTML ATL

1. Compile el proyecto. Desde el **compilar** menú, haga clic en **compilar solución**.

1. Cuando se complete la compilación, abra **Test Container**. Consulte [Probar propiedades y eventos con un contenedor de prueba](../mfc/testing-properties-and-events-with-test-container.md) para obtener información sobre cómo acceder a **Test Container**.

1. En **Test Container**, desde el **editar** menú, haga clic en **Insertar nuevo Control**.

1. En el **insertar Control** diálogo cuadro, seleccione el control del cuadro de lista. Recuerde que su nombre se basa en el nombre corto que especificó en el Asistente para controles ATL. Haga clic en **Aceptar**.

1. Examine el control. Tenga en cuenta que tiene una barra de desplazamiento. Use los controladores para cambiar el tamaño del control para activar la barra de desplazamiento.

1. Probar los botones del control. Cambia el color de fondo para el color indicado por el botón.

1. Cerrar **contenedor de prueba**.

A continuación, pruebe [modificar el control DHTML](../atl/modifying-the-atl-dhtml-control.md).

## <a name="see-also"></a>Vea también

[Compatibilidad con controles DHTML](../atl/atl-support-for-dhtml-controls.md)
