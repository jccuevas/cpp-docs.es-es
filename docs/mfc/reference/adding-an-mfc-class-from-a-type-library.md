---
title: Agregar una clase MFC desde una biblioteca de tipos
ms.date: 11/04/2016
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
ms.openlocfilehash: 5cd94ad6d400cf2db60131e822f430f87a129cbe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548023"
---
# <a name="adding-an-mfc-class-from-a-type-library"></a>Agregar una clase MFC desde una biblioteca de tipos

Use este asistente para crear una clase MFC desde una interfaz en una biblioteca de tipos disponible. Puede agregar una clase MFC a una [Aplicación MFC](../../mfc/reference/creating-an-mfc-application.md), un archivo [DLL de MFC](../../mfc/reference/creating-an-mfc-dll-project.md) o un [control ActiveX de MFC](../../mfc/reference/creating-an-mfc-activex-control.md).

> [!NOTE]
>  No es necesario crear un proyecto MFC con la automatización habilitada para agregar una clase desde una biblioteca de tipos.

Una biblioteca de tipos contiene una descripción binaria de las interfaces expuestas por un componente, definir los métodos junto con sus parámetros y tipos de valor devuelto. Se debe registrar la biblioteca de tipos para que aparezca en el **bibliotecas de tipos disponibles** lista Agregar clases desde el Asistente para la biblioteca de tipos. Vea "Dentro de COM distribuido: bibliotecas de tipo e integración del lenguaje" en MSDN library para obtener más información.

### <a name="to-add-an-mfc-class-from-a-type-library"></a>Para agregar una clase MFC desde una biblioteca de tipos

1. En el **el Explorador de soluciones** o [vista de clases](/visualstudio/ide/viewing-the-structure-of-code), haga clic en el nombre del proyecto al que desea agregar la clase.

1. En el menú contextual, haga clic en **Agregar** y después en **Agregar clase**.

1. En el [Agregar clase](../../ide/add-class-dialog-box.md) cuadro de diálogo, en el panel Plantillas, haga clic en **clase MFC de Typelib**y, a continuación, haga clic en **abierto** para mostrar el [agregar clases a partir de la biblioteca de tipos ](../../mfc/reference/add-class-from-typelib-wizard.md).

En el asistente, puede agregar más de una clase en una biblioteca de tipos. Del mismo modo, puede agregar clases de más de una biblioteca de tipos en una única sesión del asistente.

El asistente crea una clase MFC, derivada de [COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md), para cada interfaz que agregue de la biblioteca de tipos seleccionada. `COleDispatchDriver` implementa el cliente de automatización OLE.

## <a name="see-also"></a>Vea también

[Clientes de automatización](../../mfc/automation-clients.md)<br/>
[Clientes de automatización: Usar bibliotecas de tipos](../../mfc/automation-clients-using-type-libraries.md)

