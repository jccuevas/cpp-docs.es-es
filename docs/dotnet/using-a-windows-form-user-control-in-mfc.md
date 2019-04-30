---
title: Utilizar un control de usuario de Windows Forms en MFC
ms.date: 1/08/2018
helpviewer_keywords:
- MFC [C++], Windows Forms support
- interoperability [C++], Windows Forms in MFC
- interoperability [C++], MFC
- interop [C++], Windows Forms in MFC
- interop [C++], MFC
- Windows Forms [C++], MFC support
ms.assetid: 63fb099b-1dff-469c-9e34-dab52e122fcd
ms.openlocfilehash: 38c5c37712b430b137934d441056e60f2c130f78
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384496"
---
# <a name="using-a-windows-form-user-control-in-mfc"></a>Utilizar un control de usuario de Windows Forms en MFC

Utilizando las clases de soporte técnico de formularios Windows Forms de MFC, puede hospedar controles de formularios Windows Forms en aplicaciones MFC como un control ActiveX en cuadros de diálogo MFC o vistas. Además, los formularios Windows Forms se pueden hospedar como cuadros de diálogo MFC.

Las secciones siguientes describen cómo:

- Hospedar un control de Windows Forms en un cuadro de diálogo MFC.

- Hospedar un control de usuario de Windows Forms como vista MFC.

- Hospedar un formulario Windows Forms como un cuadro de diálogo MFC.

> [!NOTE]
> Integración de formularios Windows Forms de MFC sólo funciona en los proyectos que vinculen dinámicamente a MFC (proyectos en los que `_AFXDLL` está definido).

> [!NOTE]
> Al compilar la aplicación con una copia privada (modificada) de las interfaces de formularios Windows Forms de MFC DLL (mfcmifc80.dll), no se podrá instalar en la GAC, a menos que reemplace la clave de Microsoft por su propia clave de proveedor. Para obtener más información sobre la firma de ensamblados, vea [programar con ensamblados](/dotnet/framework/app-domains/programming-with-assemblies) y [ensamblados de nombre seguro (firma de ensamblados) (C++ / c++ / CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).

Si la aplicación MFC utiliza Windows Forms, deberá redistribuir mfcmifc80.dll con la aplicación. Para obtener más información, consulte [redistribuir la biblioteca MFC](../windows/redistributing-the-mfc-library.md).

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

[Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)<br/>
[Vistas de formulario](../mfc/form-views-mfc.md)
