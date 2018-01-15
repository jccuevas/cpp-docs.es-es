---
title: Con un Windows forman el Control de usuario en MFC | Documentos de Microsoft
ms.custom: 
ms.date: 1/08/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- interoperability [C++], Windows Forms in MFC
- interoperability [C++], MFC
- interop [C++], Windows Forms in MFC
- interop [C++], MFC
- Windows Forms [C++], MFC support
ms.assetid: 63fb099b-1dff-469c-9e34-dab52e122fcd
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a3289509c0cfe6016fcace34c76f145a505ecf3b
ms.sourcegitcommit: 56f6fce7d80e4f61d45752f4c8512e4ef0453e58
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/12/2018
---
# <a name="using-a-windows-form-user-control-in-mfc"></a>Utilizar un control de usuario de Windows Forms en MFC

Con las clases de soporte de formularios Windows Forms de MFC, puede hospedar controles de formularios Windows Forms dentro de las aplicaciones MFC como un control ActiveX en cuadros de diálogo MFC o vistas. Además, los formularios Windows Forms se pueden hospedar como cuadros de diálogo MFC.

Las secciones siguientes describen cómo:

- Hospedar un control de formularios Windows Forms en un cuadro de diálogo MFC.

- Hospedar un control de usuario de formularios Windows Forms como vista MFC.

- Hospedar un formulario Windows Forms como un cuadro de diálogo MFC.

> [!NOTE]
> Integración de formularios Windows Forms de MFC funciona sólo en los proyectos que se vinculen dinámicamente a MFC (proyectos en el que `_AFXDLL` está definido).

> [!NOTE]
> Cuando se compila la aplicación mediante una copia privada (modificada) de las interfaces de formularios Windows Forms de MFC DLL (mfcmifc80.dll), no se podrá instalar en la GAC, a menos que reemplazar la clave de Microsoft con su propia clave de proveedor. Para obtener más información sobre la firma de un ensamblado, vea [programar con ensamblados](/dotnet/framework/app-domains/programming-with-assemblies) y [ensamblados de nombre seguro (firma de ensamblados) (C++ / CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).

Para aplicaciones de ejemplo utilizando formularios Windows Forms, vea [ejemplo BirthdayPicker: muestra recursos de .NET Framework con formularios Windows Forms](http://msdn.microsoft.com/ac932aed-5502-4667-be29-709bca435317), [ejemplo Calculator: calculadora de bolsillo de Windows Forms](http://msdn.microsoft.com/2283b516-3b7e-45f2-80c4-fdcfb366ce25)y [ Ejemplo Scribble: Aplicación de dibujo MDI](http://msdn.microsoft.com/f025da3e-659b-4222-b991-554a1b8b2358).

Para una aplicación de ejemplo que muestra formularios Windows Forms utilizados con MFC, vea [integración de Windows Forms y MFC](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).

Si la aplicación MFC utiliza formularios Windows Forms, debe redistribuir mfcmifc80.dll con la aplicación. Para obtener más información, consulte [redistribuir la biblioteca MFC](../ide/redistributing-the-mfc-library.md).

## <a name="in-this-section"></a>En esta sección

[Hospedar un control de usuario de Windows Forms en un cuadro de diálogo MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)

[Hospedar un control de usuario de Windows Forms como una vista de MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)

[Hospedar un control de usuario de Windows Forms como un cuadro de diálogo de MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)

## <a name="reference"></a>Referencia

[CWinFormsControl (clase)](../mfc/reference/cwinformscontrol-class.md)

[CWinFormsDialog (clase)](../mfc/reference/cwinformsdialog-class.md)

[CWinFormsView (clase)](../mfc/reference/cwinformsview-class.md)

[ICommandSource (interfaz)](../mfc/reference/icommandsource-interface.md)

[ICommandTarget (interfaz)](../mfc/reference/icommandtarget-interface.md)

[ICommandUI (interfaz)](../mfc/reference/icommandui-interface.md)

[IView (interfaz)](../mfc/reference/iview-interface.md)

[CommandHandler](../atl/commandhandler.md)

[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)

[UICheckState](../mfc/reference/uicheckstate-enumeration.md)

## <a name="related-sections"></a>Secciones relacionadas

[Windows Forms](/dotnet/framework/winforms/index)

[Controles de formularios Windows Forms](/dotnet/framework/winforms/controls/index)

## <a name="see-also"></a>Vea también

[Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)  
[Vistas de formulario](../mfc/form-views-mfc.md)  
