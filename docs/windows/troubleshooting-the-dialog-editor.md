---
title: Solucionar problemas del Editor de cuadro de diálogo (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], troubleshooting
- Dialog Editor [C++], troubleshooting
- dialog boxes [C++], troubleshooting
- InitCommonControls
- RichEdit 1.0 control
- rich edit controls [C++], RichEdit 1.0
ms.assetid: 21882868-5ac4-4a41-a4a6-eaaa059402ea
ms.openlocfilehash: fe0fe704b5c17d0db4e3419f29d21f0e60bc4211
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484960"
---
# <a name="troubleshooting-the-dialog-editor-c"></a>Solucionar problemas del Editor de cuadro de diálogo (C++)

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

A continuación se muestran algunos problemas de los cuales debe tener en cuenta cuando se trabaja en C++ **diálogo** editor:

## <a name="adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function"></a>Al agregar controles a un cuadro de diálogo, el cuadro de diálogo ya no funcione

Después de agregar un control común o un control rich edit a un cuadro de diálogo, pero no aparecerá cuando se prueba el cuadro de diálogo o no aparecerá el cuadro de diálogo.

### <a name="example-of-the-problem"></a>Ejemplo del problema

1. Cree un proyecto de Win32, modifique la configuración de la aplicación para crear una aplicación de Windows (no una aplicación de consola).

1. En [vista de recursos](../windows/resource-view-window.md), haga doble clic en el archivo .rc.

1. En la opción de cuadro de diálogo, haga doble clic en el **sobre** cuadro.

1. Agregar un **Control de dirección IP** al cuadro de diálogo.

1. Guardar y **volver a generar todo**.

1. Ejecute el programa.

1. En el cuadro de diálogo **ayuda** menú, haga clic en el **sobre** comando; ningún cuadro de diálogo se muestra el cuadro.

### <a name="the-cause"></a>La causa

Actualmente, el **diálogo** editor no agrega automáticamente código al proyecto cuando arrastra y coloca los siguientes controles comunes o controles rich edit en un cuadro de diálogo. Ni Visual Studio proporciona un error o una advertencia cuando se produce este problema. Para solucionar el problema, agregue el código para el control manualmente.

||||
|-|-|-|
|Control deslizante|Control de árbol|Date Time Picker|
|Control de número|Control de pestaña|Calendario mensual|
|Control de progreso|Control de animación|IP Address Control|
|Tecla de acceso rápido|Control Rich Edit|Cuadro combinado extendido|
|Control de lista|Control Rich Edit 2.0|Control personalizado|

### <a name="fix-for-common-controls"></a>Corrección para controles comunes

Para usar controles comunes en un cuadro de diálogo, debe llamar a [InitCommonControlsEx](/windows/desktop/api/commctrl/nf-commctrl-initcommoncontrolsex) o `AFXInitCommonControls` antes de crear el cuadro de diálogo.

### <a name="fix-for-richedit-controls"></a>Corrección para controles RichEdit

Debe llamar a `LoadLibrary` para controles rich edit. Para obtener más información, consulte [acerca de los controles Rich Edit](/windows/desktop/Controls/about-rich-edit-controls) en el SDK de Windows y [información general sobre el Control Rich Edit](../mfc/overview-of-the-rich-edit-control.md).

### <a name="requirements"></a>Requisitos

Win32

## <a name="using-the-richedit-10-control-with-mfc"></a>Utilizar el control RichEdit 1.0 con MFC

Para utilizar un control RichEdit, primero debe llamar a [AfxInitRichEdit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2) para cargar el Control RichEdit 2.0 (RICHED20. Archivo DLL), o llamar a [AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit) para cargar el Control RichEdit 1.0 anterior (RICHED32. (DLL).

Puede usar actual [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) clase con el control RichEdit 1.0 anterior, pero `CRichEditCtrl` sólo está diseñada para admitir el control RichEdit 2.0. Porque RichEdit 1.0 y 2.0 RichEdit son similares, funcionará la mayoría de los métodos. Sin embargo, observe que hay algunas diferencias entre los controles 1.0 y 2.0, por lo que algunos métodos podrían no funcionen correctamente o no funcionará en absoluto.

### <a name="requirements"></a>Requisitos

MFC

## <a name="see-also"></a>Vea también

[Editor de cuadros de diálogo](../windows/dialog-editor.md)