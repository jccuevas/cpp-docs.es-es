---
title: Hospedaje de Windows Forms Control de usuario como vista MFC | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms controls [C++], hosting as an MFC view
- hosting Windows Forms control [C++]
ms.assetid: 43c02ab4-1366-434c-a980-0b19326d6ea0
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7e4e0b7bc081d3b16b3f9aa55719d298f710cdab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="hosting-a-windows-forms-user-control-as-an-mfc-view"></a>Hospedar un control de usuario de Windows Forms como vista de MFC
MFC utiliza la clase CWinFormsView para hospedar un control de usuario de formularios Windows Forms en una vista MFC. Vistas de formularios Windows Forms de MFC son controles ActiveX. El control de usuario se hospeda como elemento secundario de la vista nativa y ocupa toda el área cliente de la vista nativa.  
  
 El resultado final es similar al modelo utilizado por el [clase CFormView](../mfc/reference/cformview-class.md). Esto le permite aprovechar las ventajas del Diseñador de formularios Windows Forms y en tiempo de ejecución para crear vistas basadas en formulario enriquecidas.  
  
 Dado que las vistas de formularios Windows Forms de MFC son controles ActiveX, no tienen el mismo `hwnd` como vistas MFC. Tampoco se puede pasar como un puntero a un [CView](../mfc/reference/cview-class.md) vista. En general, use métodos de .NET Framework para trabajar con vistas de formularios Windows Forms y descarte en Win32.  
  
 Para una aplicación de ejemplo que muestra formularios Windows Forms utilizados con MFC, vea [integración de Windows Forms y MFC](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).  
  
## <a name="in-this-section"></a>En esta sección  
 [Cómo: Crear el control de usuario y hospedarlo en una vista MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)  
  
 [Cómo: Agregar enrutamientos de comandos al control de Windows Forms](../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)  
  
 [Cómo: Llamar a propiedades y métodos del control de formularios Windows Forms](../dotnet/how-to-call-properties-and-methods-of-the-windows-forms-control.md)  
  
## <a name="see-also"></a>Vea también  
 [Uso de un Control de usuario de Windows Forms en MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)   
 [Cómo: Crear controles compuestos](/dotnet/framework/winforms/controls/how-to-author-composite-controls)