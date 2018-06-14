---
title: Agregar una clase desde un control ActiveX (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], adding classes
- classes [C++], creating
ms.assetid: 729fcb37-54b8-44d5-9b4e-50bb16e0eea4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 793adf38da33808371a0df71f671c3e29da75326
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322411"
---
# <a name="adding-a-class-from-an-activex-control-visual-c"></a>Agregar una clase desde un control ActiveX (Visual C++)
Use este asistente para crear una clase MFC desde una interfaz en un control ActiveX disponible. Puede agregar una clase MFC a una [Aplicación MFC](../mfc/reference/creating-an-mfc-application.md), un archivo [DLL de MFC](../mfc/reference/creating-an-mfc-dll-project.md) o un [control ActiveX de MFC](../mfc/reference/creating-an-mfc-activex-control.md).  
  
> [!NOTE]
>  No es necesario crear un proyecto MFC con Automation habilitado para poder agregar una clase desde un control ActiveX.  
  
 Un control ActiveX es un componente de software reutilizable, basado en el modelo de objetos componentes (COM), que admite una gran variedad de funciones OLE y se puede personalizar de modo que se adapte a las necesidades del software. Los controles ActiveX están diseñados para su uso tanto en contenedores de controles ActiveX estándar como en páginas web de Internet.  
  
### <a name="to-add-an-mfc-class-from-an-activex-control"></a>Para agregar una clase MFC desde un control ActiveX  
  
1.  En el **Explorador de soluciones** o la [Vista de clases](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), haga clic con el botón derecho en el nombre del proyecto al que quiera agregar la clase de control ActiveX.  
  
2.  En el menú contextual, haga clic en **Agregar** y después en **Agregar clase**.  
  
3.  En el cuadro de diálogo [Agregar clase](../ide/add-class-dialog-box.md), en el panel Plantillas, haga clic en **Clase MFC de un control ActiveX** y, después, en **Abrir** para mostrar el [Asistente para agregar clases a partir de un control ActiveX](../ide/add-class-from-activex-control-wizard.md).  
  
 En el asistente, se puede agregar más de una interfaz en un control ActiveX. Del mismo modo, se pueden crear clases a partir de más de un control ActiveX en una única sesión del asistente.  
  
 Puede agregar clases desde controles ActiveX registrados en el sistema, o bien desde controles ActiveX situados en archivos de biblioteca de tipos (.tlb, .olb, .dll, .ocx o .exe) sin registrarlos primero en el sistema. Vea [Registro de controles OLE](../mfc/reference/registering-ole-controls.md) para obtener más información sobre cómo registrar controles ActiveX.  
  
 El asistente crea una clase MFC, derivada de [CWnd](../mfc/reference/cwnd-class.md) o de [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md), para cada interfaz que se agregue desde el control ActiveX seleccionado.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX de MFC](../mfc/mfc-activex-controls.md)   
 [Introducción a COM y ATL](../atl/introduction-to-com-and-atl.md)