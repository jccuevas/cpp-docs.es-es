---
title: Procedimiento Agregar controles de cinta y controladores de eventos
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [MFC], adding
- ribbon controls [MFC], adding
ms.assetid: b31f25bc-ede7-49c3-9e3c-dffe4e174a69
ms.openlocfilehash: c21e8b86962ebf37ca1a06bae056d09b9a9dbb2f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389520"
---
# <a name="how-to-add-ribbon-controls-and-event-handlers"></a>Procedimiento Agregar controles de cinta y controladores de eventos

Los controles de cinta de opciones son elementos, como botones y cuadros combinados, que se agregan a los paneles. Los paneles son áreas de la barra de cinta de opciones que muestran un grupo de controles relacionados.

En este tema, abra el Diseñador de cinta, agregará un botón y, a continuación, vincule un evento que muestra "Hello World".

### <a name="to-open-the-ribbon-designer"></a>Para abrir el Diseñador de cinta

1. En Visual Studio, en el **vista** menú, haga clic en **vista de recursos**.

1. En **vista de recursos**, haga doble clic en el recurso de cinta para que se muestre en la superficie de diseño.

### <a name="to-add-a-button-and-an-event-handler"></a>Para agregar un botón y un controlador de eventos

1. Desde el **barra de herramientas**, haga clic en **botón** y arrástrelo hasta un panel en la superficie de diseño.

1. Haga clic en el botón y haga clic en **Add Event Handler**.

1. En el **Asistente para controladores de eventos**, confirme la configuración predeterminada y haga clic en **agregar y editar**. Para obtener más información, consulte [Asistente para controladores de eventos](../ide/event-handler-wizard.md).

1. En el editor de código, agregue el código siguiente en la función de controlador:

```
    MessageBox((LPCTSTR)L"Hello World");
```

## <a name="see-also"></a>Vea también

[Ejemplo RibbonGadgets: Aplicación de Gadgets de cinta](../overview/visual-cpp-samples.md)<br/>
[Diseñador de la cinta de opciones (MFC)](../mfc/ribbon-designer-mfc.md)
