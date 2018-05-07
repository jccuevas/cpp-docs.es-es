---
title: Agregar una clase MFC desde una biblioteca de tipos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 349d06d7fecb82af64fbf2d3b2ebe54689b3b292
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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
  
 El asistente crea una clase MFC, derivada de [COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md), para cada interfaz que agregue de la biblioteca de tipos seleccionada. `COleDispatchDriver` implementa el cliente de automatización OLE.  
  
## <a name="see-also"></a>Vea también  
 [Clientes de automatización](../../mfc/automation-clients.md)   
 [Clientes de automatización: Usar bibliotecas de tipos](../../mfc/automation-clients-using-type-libraries.md)

