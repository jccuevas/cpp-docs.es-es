---
title: "Controles ActiveX MFC: Crear un servidor de automatización | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Automation servers [MFC], MFC ActiveX controls
- ActiveX controls [MFC], Automation server
- MFC ActiveX controls [MFC], Automation server
ms.assetid: e0c24ed2-d61c-49ad-a4fa-4e1098d1d39b
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8c3de04fbbfa9f2d0b55b7e31ca02faeddfa5c12
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-creating-an-automation-server"></a>Controles ActiveX MFC: Crear un servidor de Automation
Puede desarrollar un control ActiveX de MFC como un servidor de automatización con el fin de incrustar ese control en otra aplicación y llamar a métodos en el control de la aplicación mediante programación. Este tipo de control todavía estaría disponible se aloje en un contenedor de controles ActiveX.  
  
### <a name="to-create-a-control-as-an-automation-server"></a>Para crear un control como un servidor de automatización  
  
1.  [Crear](../mfc/reference/mfc-activex-control-wizard.md) el control.  
  
2.  [Agregar métodos](../mfc/mfc-activex-controls-methods.md).  
  
3.  Invalidar [IsInvokeAllowed](../mfc/reference/colecontrol-class.md#isinvokeallowed). Para obtener más información, vea el artículo de Knowledge Base Q146120.  
  
4.  Compilar el control.  
  
### <a name="to-programmatically-access-the-methods-in-an-automation-server"></a>Para obtener acceso mediante programación a los métodos en un servidor de automatización  
  
1.  Crear una aplicación, por ejemplo, una [exe MFC](../mfc/reference/mfc-application-wizard.md).  
  
2.  Al principio de la `InitInstance` funcionar, agregue la siguiente línea:  
  
     [!code-cpp[NVC_MFC_AxCont#17](../mfc/codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_1.cpp)]  
  
3.  En la vista de clases, haga clic en el nodo del proyecto y seleccione **agregar clases a partir de la biblioteca de tipos** para importar la biblioteca de tipos.  
  
     Esto agregará archivos con las extensiones de archivo .h y .cpp al proyecto.  
  
4.  En el archivo de encabezado de la clase donde llamará a uno o varios métodos en el control ActiveX, agregue la siguiente línea: `#include filename.h`, donde el nombre de archivo es el nombre del archivo de encabezado que se creó cuando se importa la biblioteca de tipos.  
  
5.  En la función donde se realizará una llamada a un método en el control ActiveX, agregue código que crea un objeto de clase de contenedor del control y crear el objeto ActiveX. Por ejemplo, el siguiente código MFC crea un `CCirc` control, obtiene la propiedad Caption y muestra el resultado cuando se hace clic en el botón Aceptar en un cuadro de diálogo:  
  
     [!code-cpp[NVC_MFC_AxCont#18](../mfc/codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_2.cpp)]  
  
 Si agrega métodos al control ActiveX después de usarlo en una aplicación, puede comenzar a usar la versión más reciente del control en la aplicación mediante la eliminación de los archivos que se crearon cuando se importa la biblioteca de tipos. A continuación, vuelva a importar la biblioteca de tipos.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

