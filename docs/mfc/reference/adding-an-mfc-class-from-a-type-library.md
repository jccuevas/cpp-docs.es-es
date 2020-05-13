---
title: Agregar una clase MFC desde una biblioteca de tipos
ms.date: 11/04/2016
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
ms.openlocfilehash: bf9c763a215a4880d5b0ad206f6a347341fea9eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371721"
---
# <a name="adding-an-mfc-class-from-a-type-library"></a>Agregar una clase MFC desde una biblioteca de tipos

Utilice este asistente para crear una clase MFC a partir de una interfaz en una biblioteca de tipos disponible. Puede agregar una clase MFC a una [Aplicación MFC](../../mfc/reference/creating-an-mfc-application.md), un archivo [DLL de MFC](../../mfc/reference/creating-an-mfc-dll-project.md) o un [control ActiveX de MFC](../../mfc/reference/creating-an-mfc-activex-control.md).

> [!NOTE]
> No es necesario crear el proyecto MFC con Automatización habilitada para agregar una clase desde una biblioteca de tipos.

Una biblioteca de tipos contiene una descripción binaria de las interfaces expuestas por un componente, definiendo los métodos junto con sus parámetros y tipos de valor devuelto. La biblioteca de tipos debe estar registrada para que aparezca en la lista Bibliotecas de tipos **disponibles** del Asistente para agregar clases desde Typelib. Consulte "Inside Distributed COM: Type Libraries and Language Integration" en la biblioteca MSDN para obtener más información.

### <a name="to-add-an-mfc-class-from-a-type-library"></a>Para agregar una clase MFC desde una biblioteca de tipos

1. En **el Explorador** de soluciones o en la vista de [clases](/visualstudio/ide/viewing-the-structure-of-code), haga clic con el botón secundario en el nombre del proyecto al que desea agregar la clase.

1. En el menú contextual, haga clic en **Agregar**y, a continuación, haga clic en **Agregar clase**.

1. En el cuadro de diálogo [Agregar clase,](../../ide/add-class-dialog-box.md) en el panel Plantillas , haga clic en **Clase MFC desde Typelib**y, a continuación, haga clic en **Abrir** para mostrar el Asistente para [agregar clases desde Typelib](../../mfc/reference/add-class-from-typelib-wizard.md).

En el asistente, puede agregar más de una clase en una biblioteca de tipos. Del mismo modo, puede agregar clases de más de una biblioteca de tipos en una sola sesión del asistente.

El asistente crea una clase MFC, derivada de [COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md), para cada interfaz que agregue desde la biblioteca de tipos seleccionada. `COleDispatchDriver`implementa el lado cliente de la automatización OLE.

## <a name="see-also"></a>Consulte también

[Clientes de automatización](../../mfc/automation-clients.md)<br/>
[Clientes de Automation: Usar bibliotecas de tipos](../../mfc/automation-clients-using-type-libraries.md)
