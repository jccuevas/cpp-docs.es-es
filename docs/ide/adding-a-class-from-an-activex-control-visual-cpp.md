---
title: Agregar una clase desde un Control ActiveX (Visual C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ActiveX controls [C++], adding classes
- classes [C++], creating
ms.assetid: 729fcb37-54b8-44d5-9b4e-50bb16e0eea4
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2357e3d3bf06a1f9d3216b1e0b93a6f80949b9ed
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="adding-a-class-from-an-activex-control-visual-c"></a>Agregar una clase desde un control ActiveX (Visual C++)
Use este asistente para crear una clase MFC desde una interfaz en un control ActiveX disponible. Puede agregar una clase MFC a un [aplicación MFC](../mfc/reference/creating-an-mfc-application.md), [DLL de MFC](../mfc/reference/creating-an-mfc-dll-project.md), o un [control ActiveX de MFC](../mfc/reference/creating-an-mfc-activex-control.md).  
  
> [!NOTE]
>  No es necesario crear un proyecto MFC con la automatización habilitada para poder agregar una clase desde un control ActiveX.  
  
 Un control ActiveX es un componente de software reutilizable, basado en el modelo de objetos componentes (COM), que admite una gran variedad de funciones OLE y se puede personalizar de modo que se adapte a las necesidades del software. Controles ActiveX están diseñados para su uso tanto en contenedores de controles ActiveX ordinarios como en páginas Web de Internet.  
  
### <a name="to-add-an-mfc-class-from-an-activex-control"></a>Para agregar una clase MFC desde un control ActiveX  
  
1.  En la vista **el Explorador de soluciones** o [vista de clases](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), haga clic en el nombre del proyecto al que desea agregar la clase del control ActiveX.  
  
2.  En el menú contextual, haga clic en **agregar**y, a continuación, haga clic en **Agregar clase**.  
  
3.  En el [Agregar clase](../ide/add-class-dialog-box.md) cuadro de diálogo, en el panel Plantillas, haga clic en **clase MFC de un ActiveX Control**y, a continuación, haga clic en **abiertos** para mostrar el [Agregar clase de ActiveX Control Asistente para](../ide/add-class-from-activex-control-wizard.md).  
  
 En el asistente, puede agregar más de una interfaz en un control ActiveX. Del mismo modo, puede crear clases de más de un control ActiveX en una única sesión del asistente.  
  
 Puede agregar clases de controles ActiveX registrados en el sistema, o puede agregar clases de controles ActiveX situados en archivos de biblioteca de tipos (.tlb, .olb, .dll, .ocx o .exe) sin registrarlos primero en el sistema. Vea [registrar controles OLE](../mfc/reference/registering-ole-controls.md) para obtener más información sobre cómo registrar controles ActiveX.  
  
 El asistente crea una clase MFC, derivada de [CWnd](../mfc/reference/cwnd-class.md) o de [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md), para cada interfaz que se agregue desde el control ActiveX seleccionado.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX de MFC](../mfc/mfc-activex-controls.md)   
 [Introducción a COM y ATL](../atl/introduction-to-com-and-atl.md)