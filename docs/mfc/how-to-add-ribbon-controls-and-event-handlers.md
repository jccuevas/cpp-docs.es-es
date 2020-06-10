---
title: 'Cómo: Agregar controles de cinta y controladores de eventos'
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [MFC], adding
- ribbon controls [MFC], adding
ms.assetid: b31f25bc-ede7-49c3-9e3c-dffe4e174a69
ms.openlocfilehash: 560524c36dbf57faec3b4b6372cade047f9fe7de
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618481"
---
# <a name="how-to-add-ribbon-controls-and-event-handlers"></a>Cómo: Agregar controles de cinta y controladores de eventos

Los controles de la cinta de opciones son elementos, como botones y cuadros combinados, que se agregan a los paneles. Los paneles son áreas de la barra de cinta que muestran un grupo de controles relacionados.

En este tema, abrirá el diseñador de la cinta de opciones, agregará un botón y, a continuación, vinculará un evento que muestra "Hola mundo".

### <a name="to-open-the-ribbon-designer"></a>Para abrir el diseñador de la cinta de opciones

1. En Visual Studio, en el menú **Ver** , haga clic en **vista de recursos**.

1. En **vista de recursos**, haga doble clic en el recurso de la cinta de opciones para mostrarlo en la superficie de diseño.

### <a name="to-add-a-button-and-an-event-handler"></a>Para agregar un botón y un controlador de eventos

1. En la **barra de herramientas**, haga clic en **botón** y arrástrelo hasta un panel en la superficie de diseño.

1. Haga clic con el botón secundario en el botón y haga clic en **Agregar controlador de eventos**.

1. En el **Asistente para controladores de eventos**, confirme la configuración predeterminada y haga clic en **Agregar y editar**. Para obtener más información, vea [Asistente para controladores de eventos](../ide/event-handler-wizard.md).

1. En el editor de código, agregue el código siguiente a la función de controlador:

```
    MessageBox((LPCTSTR)L"Hello World");
```

## <a name="see-also"></a>Consulte también

[Ejemplo RibbonGadgets: aplicación gadgets de la cinta de opciones](../overview/visual-cpp-samples.md)<br/>
[Diseñador de la cinta de opciones (MFC)](ribbon-designer-mfc.md)
