---
title: Utilizar un control de usuario de Windows Forms en MFC
ms.date: 01/08/2018
helpviewer_keywords:
- MFC [C++], Windows Forms support
- interoperability [C++], Windows Forms in MFC
- interoperability [C++], MFC
- interop [C++], Windows Forms in MFC
- interop [C++], MFC
- Windows Forms [C++], MFC support
ms.assetid: 63fb099b-1dff-469c-9e34-dab52e122fcd
ms.openlocfilehash: efabbf84778d925ec1de03f5f4ea0ca09185bd81
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "79544751"
---
# <a name="using-a-windows-form-user-control-in-mfc"></a>Utilizar un control de usuario de Windows Forms en MFC

Con las clases de compatibilidad de Windows Forms MFC, puede hospedar controles de Windows Forms dentro de las aplicaciones MFC como un control ActiveX en los cuadros de diálogo o vistas de MFC. Además, Windows Forms formularios se pueden hospedar como cuadros de diálogo de MFC.

En las secciones siguientes se describe cómo:

- Hospede un control de Windows Forms en un cuadro de diálogo de MFC.

- Hospede un control de usuario Windows Forms como una vista MFC.

- Hospede un formulario Windows Forms como un cuadro de diálogo de MFC.

> [!NOTE]
> La integración de Windows Forms MFC solo funciona en proyectos que se vinculan dinámicamente con MFC (proyectos en los que se define `_AFXDLL`).

> [!NOTE]
> Al compilar la aplicación mediante una copia privada (modificada) del archivo DLL de interfaces Windows Forms MFC (mfcmifc80. dll), no podrá instalarse en la GAC a menos que reemplace la clave de Microsoft por su propia clave de proveedor. Para obtener más información sobre la firma de ensamblados, vea [programar con ensamblados](/dotnet/framework/app-domains/programming-with-assemblies) y [ensamblados deC++nombre seguro (la firma de ensamblados) (/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).

Si la aplicación MFC utiliza Windows Forms, deberá redistribuir mfcmifc80. dll con su aplicación. Para obtener más información, vea [redistribuir la biblioteca MFC](../windows/redistributing-the-mfc-library.md).

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

[Uicheckstate (](../mfc/reference/uicheckstate-enumeration.md)

## <a name="related-sections"></a>Secciones relacionadas

[Windows Forms](/dotnet/framework/winforms/index)

[Controles de Windows Forms](/dotnet/framework/winforms/controls/index)

## <a name="see-also"></a>Consulte también

[Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)<br/>
[Vistas de formulario](../mfc/form-views-mfc.md)
