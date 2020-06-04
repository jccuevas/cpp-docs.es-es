---
title: Servicios especiales de CWinApp
ms.date: 11/04/2016
f1_keywords:
- LoadStdProfileSettings
- EnableShellOpen
helpviewer_keywords:
- files [MFC], most recently used
- DragAcceptFiles method [MFC]
- MRU lists
- GDI+, initializing for MFC
- GDI+, suppressing background thread [MFC]
- CWinApp class [MFC], shell registration
- application objects [MFC], services
- CWinApp class [MFC], initializing GDI+
- MFC, shell registration
- CWinApp class [MFC], File Manager drag and drop
- LoadStdProfileSettings method [MFC]
- MFC, most-recently-used file list
- RegisterShellFileTypes method [MFC]
- drag and drop [MFC], files
- registering file types
- Shell, registering file types
- services, provided by CWinApp
- CWinApp class [MFC], recently used documents
- CWinApp class [MFC], services
- files [MFC], drag and drop
- EnableShellOpen method [MFC]
- registry [MFC], most recently used files
- MFC, file operations
- registration [MFC], shell
ms.assetid: 0480cd01-f629-4249-b221-93432d95b431
ms.openlocfilehash: 1f5abcdab3eda1304879b122acc8072951a0e6c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363901"
---
# <a name="special-cwinapp-services"></a>Servicios especiales de CWinApp

Además de ejecutar el bucle de mensajes y darle la oportunidad de inicializar la aplicación y limpiar después de ella, [CWinApp](../mfc/reference/cwinapp-class.md) proporciona varios otros servicios.

## <a name="shell-registration"></a><a name="_core_shell_registration"></a>Registro de Shell

De forma predeterminada, el Asistente para aplicaciones MFC permite al usuario abrir archivos de datos que la aplicación ha creado haciendo doble clic en ellos en el Explorador de archivos o el Administrador de archivos. Si la aplicación es una aplicación MDI y especifica una extensión para los archivos que crea la aplicación, el Asistente para aplicaciones `InitInstance` MFC agrega llamadas a las funciones miembro [RegisterShellFileTypes](../mfc/reference/cwinapp-class.md#registershellfiletypes) y [EnableShellOpen](../mfc/reference/cwinapp-class.md#enableshellopen) de [CWinApp](../mfc/reference/cwinapp-class.md) a la invalidación que escribe automáticamente.

`RegisterShellFileTypes`registra los tipos de documentos de la aplicación con el Explorador de archivos o el Administrador de archivos. La función agrega entradas a la base de datos de registro que Windows mantiene. Las entradas registran cada tipo de documento, asocian una extensión de archivo con el tipo de archivo, especifican una línea de comandos para abrir la aplicación y especifican un comando de intercambio dinámico de datos (DDE) para abrir un documento de ese tipo.

`EnableShellOpen`completa el proceso permitiendo que la aplicación reciba comandos DDE desde el Explorador de archivos o el Administrador de archivos para abrir el archivo elegido por el usuario.

Este soporte de `CWinApp` registro automático elimina la necesidad de enviar un archivo .reg con su aplicación o de realizar trabajos de instalación especiales.

Si desea inicializar GDI+ para la aplicación (mediante una llamada a [GdiplusStartup](/windows/win32/api/gdiplusinit/nf-gdiplusinit-gdiplusstartup) en la función [InitInstance),](../mfc/reference/cwinapp-class.md#initinstance) debe suprimir el subproceso en segundo plano de GDI+GDI+.

Puede hacerlo estableciendo `SuppressBackgroundThread` el miembro de la estructura [GdiplusStartupInput](/windows/win32/api/gdiplusinit/ns-gdiplusinit-gdiplusstartupinput) en **TRUE**. Al suprimir el subproceso en segundo `NotificationHook` `NotificationUnhook` plano GDI+, las llamadas y deben realizarse justo antes de entrar y salir del bucle de mensajes de la aplicación. Para obtener más información sobre estas llamadas, vea [GdiplusStartupOutput](/windows/win32/api/gdiplusinit/ns-gdiplusinit-gdiplusstartupoutput). Por lo tanto, `GdiplusStartup` un buen lugar para llamar y las funciones de notificación de enlace estaría en una invalidación de la función virtual [CWinApp::Run](../mfc/reference/cwinapp-class.md#run), como se muestra a continuación:

[!code-cpp[NVC_MFCDocView#6](../mfc/codesnippet/cpp/special-cwinapp-services_1.cpp)]

Si no suprime el subproceso GDI+, los comandos DDE se pueden emitir prematuramente a la aplicación antes de que se haya creado su ventana principal. Los comandos DDE emitidos por el shell se pueden anular prematuramente, lo que da lugar a mensajes de error.

## <a name="file-manager-drag-and-drop"></a><a name="_core_file_manager_drag_and_drop"></a>Administrador de archivos Arrastrar y soltar

Los archivos se pueden arrastrar desde la ventana de vista de archivos en el Administrador de archivos o el Explorador de archivos a una ventana de la aplicación. Por ejemplo, puede habilitar uno o varios archivos para arrastrarlos a la ventana principal de una aplicación MDI, donde la aplicación podría recuperar los nombres de archivo y abrir ventanas secundarias MDI para esos archivos.

Para habilitar la arrastrar y colocar archivos en la aplicación, el Asistente para aplicaciones MFC escribe una `InitInstance`llamada a la función miembro de [CWnd](../mfc/reference/cwnd-class.md) [DragAcceptFiles](../mfc/reference/cwnd-class.md#dragacceptfiles) para la ventana de marco principal en el archivo . Puede quitar esa llamada si no desea implementar la característica de arrastrar y colocar.

> [!NOTE]
> También puede implementar capacidades de arrastrar y colocar más generales (arrastrar datos entre documentos o dentro de ellos) con OLE. Para obtener información, consulte el artículo [arrastrar y colocar OLE](../mfc/drag-and-drop-ole.md).

## <a name="keeping-track-of-the-most-recently-used-documents"></a><a name="_core_keeping_track_of_the_most_recently_used_documents"></a>Realizar un seguimiento de los documentos usados más recientemente

A medida que el usuario abre y cierra archivos, el objeto de aplicación realiza un seguimiento de los cuatro archivos utilizados más recientemente. Los nombres de estos archivos se agregan al menú Archivo y se actualizan cuando cambian. El marco de trabajo almacena estos nombres de archivo en el registro o en el archivo .ini, con el mismo nombre que el proyecto y los lee del archivo cuando se inicia la aplicación. La `InitInstance` invalidación que el Asistente para aplicaciones MFC crea automáticamente incluye una llamada a la función miembro de [CWinApp](../mfc/reference/cwinapp-class.md) [LoadStdProfileSettings](../mfc/reference/cwinapp-class.md#loadstdprofilesettings), que carga información del registro o del archivo .ini, incluidos los nombres de archivo usados más recientemente.

Estas entradas se almacenan de la siguiente manera:

- En Windows NT, Windows 2000 y versiones posteriores, el valor se almacena en una clave del Registro.

- En Windows 3.x, el valor se almacena en WIN. Archivo INI.

- En Windows 95 y versiones posteriores, el valor se almacena en una versión almacenada en caché de WIN. Ini.

## <a name="see-also"></a>Consulte también

[CWinApp: la clase Application](../mfc/cwinapp-the-application-class.md)
