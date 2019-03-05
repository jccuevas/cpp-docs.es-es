---
title: 'Controles ActiveX MFC: Creación de un servidor de automatización'
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers [MFC], MFC ActiveX controls
- ActiveX controls [MFC], Automation server
- MFC ActiveX controls [MFC], Automation server
ms.assetid: e0c24ed2-d61c-49ad-a4fa-4e1098d1d39b
ms.openlocfilehash: 01f0162e124c5c49d45ce4a90f5243c88b09b5a0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57303734"
---
# <a name="mfc-activex-controls-creating-an-automation-server"></a>Controles ActiveX MFC: Creación de un servidor de automatización

Puede desarrollar un control ActiveX de MFC como un servidor de automatización con el fin de incrustación de ese control en otra aplicación y llamar a métodos en el control desde la aplicación mediante programación. Este tipo de control todavía estaría disponible para hospedarse en un contenedor de controles ActiveX.

### <a name="to-create-a-control-as-an-automation-server"></a>Para crear un control como un servidor de automatización

1. [Crear](../mfc/reference/mfc-activex-control-wizard.md) el control.

1. [Agregue métodos](../mfc/mfc-activex-controls-methods.md).

1. Invalidar [IsInvokeAllowed](../mfc/reference/colecontrol-class.md#isinvokeallowed).

1. Compilar el control.

### <a name="to-programmatically-access-the-methods-in-an-automation-server"></a>Acceso mediante programación a los métodos en un servidor de automatización

1. Crear una aplicación, por ejemplo, un [exe de MFC](../mfc/reference/mfc-application-wizard.md).

1. Al principio de la `InitInstance` de función, agregue la siguiente línea:

   [!code-cpp[NVC_MFC_AxCont#17](../mfc/codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_1.cpp)]

1. En la vista de clases, haga clic en el nodo del proyecto y seleccione **Agregar clase de typelib** para importar la biblioteca de tipos.

   Esto agregará los archivos con las extensiones de archivo .h y .cpp al proyecto.

1. En el archivo de encabezado de la clase donde se llamará a uno o varios métodos en el control ActiveX, agregue la siguiente línea: `#include filename.h`, donde el nombre de archivo es el nombre del archivo de encabezado que se creó cuando se importa la biblioteca de tipos.

1. En la función donde se realizará una llamada a un método en el control ActiveX, agregue código que crea un objeto de clase contenedora del control y crear el objeto ActiveX. Por ejemplo, el siguiente código MFC crea un `CCirc` control, obtiene la propiedad Caption y muestra el resultado cuando se hace clic en el botón Aceptar en un cuadro de diálogo:

   [!code-cpp[NVC_MFC_AxCont#18](../mfc/codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_2.cpp)]

Si agrega métodos al control ActiveX después de usarlo en una aplicación, puede empezar a usar la versión más reciente del control en la aplicación mediante la eliminación de los archivos que se crearon cuando se importa la biblioteca de tipos. A continuación, vuelva a importar la biblioteca de tipos.

## <a name="see-also"></a>Vea también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)
