---
title: "Hospedaje de una ventana de formulario el Control de usuario en un cuadro de diálogo MFC | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: da8e8a54947b329fe36eea5c80bdc13ba5cdfa74
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>Hospedar un control de usuario de Windows Forms en un cuadro de diálogo MFC
MFC hospeda un control de formularios Windows Forms como un tipo especial de control ActiveX y se comunica con el control mediante interfaces de ActiveX y propiedades y métodos de la <xref:System.Windows.Forms.Control> clase. Se recomienda usar métodos y propiedades de .NET Framework para operar en el control.  
  
 Para una aplicación de ejemplo que muestra formularios Windows Forms utilizados con MFC, vea [integración de Windows Forms y MFC](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).  
  
> [!NOTE]
>  En la versión actual, un `CDialogBar` objeto no puede hospedar controles de formularios Windows Forms.  
  
## <a name="in-this-section"></a>En esta sección  
 [Cómo: Crear el control de usuario y el host en un cuadro de diálogo](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)  
  
 [Cómo: realizar enlaces de datos DDX/DDV con formularios Windows Forms](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)  
  
 [Cómo: Recibir eventos de Windows Forms de clases nativas de C++](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)  
  
## <a name="reference"></a>Referencia  
 [Clase CWinFormsControl](../mfc/reference/cwinformscontrol-class.md) &#124; [CDialog (clase)](../mfc/reference/cdialog-class.md) &#124; [CWnd (clase)](../mfc/reference/cwnd-class.md) &#124;<xref:System.Windows.Forms.Control>  
  
## <a name="see-also"></a>Vea también  
 [Uso de un Control de usuario de Windows Forms en MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)   
 [Diferencias de programación entre Windows Forms y MFC](../dotnet/windows-forms-mfc-programming-differences.md)   
 [Hospedar un Control de usuario de Windows Forms como vista MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)   
 [Hospedar un control de usuario de Windows Forms como un cuadro de diálogo de MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)