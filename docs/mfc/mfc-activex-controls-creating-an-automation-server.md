---
title: 'Controles ActiveX MFC: Crear un servidor de automatización'
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers [MFC], MFC ActiveX controls
- ActiveX controls [MFC], Automation server
- MFC ActiveX controls [MFC], Automation server
ms.assetid: e0c24ed2-d61c-49ad-a4fa-4e1098d1d39b
ms.openlocfilehash: f2c941e43e810845560b4c35c558ec70248c21ed
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622379"
---
# <a name="mfc-activex-controls-creating-an-automation-server"></a>Controles ActiveX MFC: Crear un servidor de automatización

Puede desarrollar un control ActiveX MFC como un servidor de automatización con el fin de insertar mediante programación ese control en otra aplicación y llamar a los métodos del control desde la aplicación. Este tipo de control seguiría estando disponible para hospedarse en un contenedor de controles ActiveX.

### <a name="to-create-a-control-as-an-automation-server"></a>Para crear un control como un servidor de automatización

1. [Cree](reference/mfc-activex-control-wizard.md) el control.

1. [Agregue métodos](mfc-activex-controls-methods.md).

1. Reemplace [IsInvokeAllowed](reference/colecontrol-class.md#isinvokeallowed).

1. Compile el control.

### <a name="to-programmatically-access-the-methods-in-an-automation-server"></a>Para tener acceso mediante programación a los métodos en un servidor de automatización

1. Cree una aplicación, por ejemplo, un [archivo exe de MFC](reference/mfc-application-wizard.md).

1. Al principio de la `InitInstance` función, agregue la siguiente línea:

   [!code-cpp[NVC_MFC_AxCont#17](codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_1.cpp)]

1. En Vista de clases, haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar clase de typelib** para importar la biblioteca de tipos.

   Esto agregará los archivos con las extensiones de nombre de archivo. h y. cpp al proyecto.

1. En el archivo de encabezado de la clase en la que se llamará a uno o varios métodos del control ActiveX, agregue la siguiente línea: `#include filename.h` , donde nombre de archivo es el nombre del archivo de encabezado que se creó al importar la biblioteca de tipos.

1. En la función en la que se realizará una llamada a un método en el control ActiveX, agregue el código que crea un objeto de la clase contenedora del control y cree el objeto ActiveX. Por ejemplo, el siguiente código MFC crea una instancia de un `CCirc` control, obtiene la propiedad Caption y muestra el resultado cuando se hace clic en el botón Aceptar en un cuadro de diálogo:

   [!code-cpp[NVC_MFC_AxCont#18](codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_2.cpp)]

Si agrega métodos al control ActiveX después de utilizarlo en una aplicación, puede empezar a usar la versión más reciente del control en la aplicación eliminando los archivos que se crearon al importar la biblioteca de tipos. A continuación, vuelva a importar la biblioteca de tipos.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](mfc-activex-controls.md)
