---
title: Agregar una clase MFC desde una biblioteca de tipos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1efc61e097d7e1136fdb7b6ef740dc00342077e4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="adding-an-mfc-class-from-a-type-library"></a>Agregar una clase MFC desde una biblioteca de tipos
Use este asistente para crear una clase MFC desde una interfaz en una biblioteca de tipos disponibles. Puede agregar una clase MFC a un [aplicación MFC](../../mfc/reference/creating-an-mfc-application.md), [DLL de MFC](../../mfc/reference/creating-an-mfc-dll-project.md), o un [control ActiveX de MFC](../../mfc/reference/creating-an-mfc-activex-control.md).  
  
> [!NOTE]
>  No es necesario crear un proyecto MFC con la automatización habilitada para poder agregar una clase desde una biblioteca de tipos.  
  
 Una biblioteca de tipos contiene una descripción binaria de las interfaces expuestas por un componente, que define los métodos junto con sus parámetros y tipos de valor devuelto. La biblioteca de tipos debe estar registrada para que aparezca en el **bibliotecas de tipos disponibles** lista Agregar clases desde el Asistente para la biblioteca de tipos. Vea "Dentro de COM distribuido: bibliotecas de tipo e integración del lenguaje" en MSDN library para obtener más información.  
  
### <a name="to-add-an-mfc-class-from-a-type-library"></a>Para agregar una clase MFC desde una biblioteca de tipos  
  
1.  En la vista **el Explorador de soluciones** o [vista de clases](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), haga clic en el nombre del proyecto al que desea agregar la clase.  
  
2.  En el menú contextual, haga clic en **agregar**y, a continuación, haga clic en **Agregar clase**.  
  
3.  En el [Agregar clase](../../ide/add-class-dialog-box.md) cuadro de diálogo, en el panel Plantillas, haga clic en **clase MFC de Typelib**y, a continuación, haga clic en **abiertos** para mostrar el [agregar clases a partir de la biblioteca de tipos ](../../mfc/reference/add-class-from-typelib-wizard.md).  
  
 En el asistente, puede agregar más de una clase en una biblioteca de tipos. Del mismo modo, puede agregar clases de más de una biblioteca de tipos en una única sesión del asistente.  
  
 El asistente crea una clase MFC, derivada de [COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md), para cada interfaz que agregue de la biblioteca de tipos seleccionada. `COleDispatchDriver`implementa el cliente de automatización OLE.  
  
## <a name="see-also"></a>Vea también  
 [Clientes de automatización](../../mfc/automation-clients.md)   
 [Clientes de automatización: Usar bibliotecas de tipos](../../mfc/automation-clients-using-type-libraries.md)

