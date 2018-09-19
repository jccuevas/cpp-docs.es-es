---
title: Insertar un formulario en un proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inserting forms [MFC]
- Insert New dialog box [MFC]
- forms, adding to projects
ms.assetid: f3bd2998-3ce2-496d-ac5c-57ca70eec7cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e62618301e09ad4c44fb91608976ecab972a59da
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344138"
---
# <a name="inserting-a-form-into-a-project"></a>Insertar un formulario en un proyecto
Formularios proporcionan un contenedor adecuado para los controles. Puede insertar fácilmente un formulario basado en MFC en la aplicación siempre y cuando la aplicación es compatible con las bibliotecas MFC.  
  
### <a name="to-insert-a-form-into-your-project"></a>Para insertar un formulario en el proyecto  
  
1.  En vista de clases, seleccione el proyecto al que desea agregar el formulario y haga clic en el botón secundario del mouse.  
  
2.  En el menú contextual, haga clic en **agregar** y, a continuación, haga clic en **Agregar clase**.  
  
     Si el **nuevo formulario** comando no está disponible, el proyecto se puede basar en Active Template Library (ATL). Para agregar un formulario a un proyecto ATL, debe [especificar ciertas opciones de configuración](../atl/reference/application-settings-atl-project-wizard.md) cuando empiece a crear el proyecto.  
  
3.  Desde el **MFC** carpeta, haga clic en **clase MFC**.  
  
4.  Mediante el Asistente para la clase de MFC, asegúrese de la nueva clase se deriva [CFormView](../mfc/reference/cformview-class.md).  
  
 Visual C++ agrega el formulario a la aplicación, ábralo en el editor de cuadro de diálogo para que pueda empezar a agregar controles y trabajar en su diseño global.  
  
 Puede que desee realizar los siguientes pasos adicionales (no se aplica a las aplicaciones basadas en el cuadro de diálogo):  
  
1.  Invalidar el `OnUpdate` función miembro.  
  
2.  Implementar una función miembro para mover datos desde la vista al documento.  
  
3.  Crear un `OnPrint` función miembro.  
  
## <a name="see-also"></a>Vea también  
 [Vistas de formulario](../mfc/form-views-mfc.md)

