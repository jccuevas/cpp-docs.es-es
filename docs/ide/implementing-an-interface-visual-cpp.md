---
title: Implementar una interfaz (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interfaces, implementing
ms.assetid: 72f8731b-7e36-45db-8b10-7ef211a773cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4227f566d655911553baeb5e8162f13bc9994130
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395536"
---
# <a name="implementing-an-interface-visual-c"></a>Implementar una interfaz (Visual C++)

Para implementar una interfaz, debe haber creado un proyecto como una aplicación COM de ATL o como una aplicación MFC que sea compatible con ATL. Puede usar el [Asistente para proyectos ATL](../atl/reference/atl-project-wizard.md) para crear una aplicación ATL, o bien [agregar un objeto ATL a una aplicación MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) para implementar la compatibilidad con ATL para una aplicación MFC.

Una vez creado el proyecto, para implementar una interfaz, primero debe agregar un objeto ATL. Vea [Agregar controles y objetos a un proyecto ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) para obtener una lista de los asistentes que agregan objetos a los proyectos ATL.

> [!NOTE]
>  El asistente no admite cuadros de diálogo de ATL, servicios web XML creados con ATL, objetos de rendimiento ni contadores de rendimiento.

Si se [agrega un control ATL](../atl/reference/adding-an-atl-control.md), se puede especificar si se quieren implementar interfaces predeterminadas, enumeradas en la página [Interfaces](../atl/reference/interfaces-atl-control-wizard.md) del asistente y definidas en atlcom.h.

Después de agregar el objeto o el control, puede implementar otras interfaces, ubicadas en cualquier biblioteca de tipos disponible, mediante el Asistente para implementar interfaces.

Si va a agregar una interfaz nueva, debe agregarla de forma manual al archivo .idl del proyecto. Vea [Agregar una nueva interfaz en un proyecto ATL](../atl/reference/adding-a-new-interface-in-an-atl-project.md) para obtener más información.

### <a name="to-implement-an-interface"></a>Para implementar una interfaz

1. En la Vista de clases, haga clic con el botón derecho en el nombre de clase para el objeto ATL.

1. Haga clic en **Agregar** desde el menú contextual y, después, haga clic en **Implementar interfaz** para mostrar el [Asistente para implementar interfaces](../ide/implement-interface-wizard.md).

1. Seleccione las interfaces que se van a implementar desde las bibliotecas de tipos adecuadas y haga clic en **Finalizar**.

1. En la Vista de clases, expanda el nodo Bases e interfaces del objeto para ver la interfaz que ha implementado y, después, expanda el nodo de la interfaz para ver sus propiedades, métodos y eventos disponibles.

   > [!NOTE]
   > También puede usar el [Examinador de objetos](/visualstudio/ide/viewing-the-structure-of-code) para examinar los miembros de la interfaz.

## <a name="see-also"></a>Vea también

[Crear una interfaz COM](../ide/creating-a-com-interface-visual-cpp.md)<br>
[Editar una interfaz COM](../ide/editing-a-com-interface.md)