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
ms.openlocfilehash: 04c7357d67dc1a5daee4b8b8135c9a54eda8504a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127834"
---
# <a name="special-cwinapp-services"></a>Servicios especiales de CWinApp

Además de ejecutar el bucle de mensajes y darle la oportunidad de inicializar la aplicación y de limpiarla después, [CWinApp](../mfc/reference/cwinapp-class.md) proporciona otros servicios.

##  <a name="_core_shell_registration"></a>Registro de Shell

De forma predeterminada, el Asistente para aplicaciones MFC permite al usuario abrir archivos de datos que la aplicación ha creado haciendo doble clic en el explorador de archivos o en el administrador de archivos. Si la aplicación es una aplicación MDI y se especifica una extensión para los archivos que crea la aplicación, el Asistente para aplicaciones MFC agrega llamadas a las funciones miembro [RegisterShellFileTypes](../mfc/reference/cwinapp-class.md#registershellfiletypes) y [EnableShellOpen](../mfc/reference/cwinapp-class.md#enableshellopen) de [CWinApp](../mfc/reference/cwinapp-class.md) al `InitInstance` invalidación que escribe.

`RegisterShellFileTypes` registra los tipos de documento de la aplicación con el explorador de archivos o el administrador de archivos. La función agrega entradas a la base de datos de registro que mantiene Windows. Las entradas registran cada tipo de documento, asocian una extensión de archivo con el tipo de archivo, especifican una línea de comandos para abrir la aplicación y especifican un comando de intercambio dinámico de datos (DDE) para abrir un documento de ese tipo.

`EnableShellOpen` completa el proceso permitiendo que la aplicación reciba comandos DDE desde el explorador de archivos o el administrador de archivos para abrir el archivo elegido por el usuario.

Esta compatibilidad con el registro automático en `CWinApp` elimina la necesidad de enviar un archivo. reg con la aplicación o de realizar un trabajo de instalación especial.

Si desea inicializar GDI+ para la aplicación (mediante una llamada a [GdiplusStartup](/windows/win32/api/gdiplusinit/nf-gdiplusinit-gdiplusstartup) en la función [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) ), debe suprimir el subproceso en segundo plano GDI+.

Puede hacerlo estableciendo el miembro `SuppressBackgroundThread` de la estructura [GdiplusStartupInput](/windows/win32/api/gdiplusinit/ns-gdiplusinit-gdiplusstartupinput) en **true**. Al suprimir el subproceso en segundo plano de GDI+, las llamadas a `NotificationHook` y `NotificationUnhook` deben realizarse justo antes de entrar y salir del bucle de mensajes de la aplicación. Para obtener más información sobre estas llamadas, vea [GdiplusStartupOutput](/windows/win32/api/gdiplusinit/ns-gdiplusinit-gdiplusstartupoutput). Por lo tanto, un buen lugar para llamar a `GdiplusStartup` y a las funciones de notificación de enlace sería una invalidación de la función virtual [CWinApp:: Run](../mfc/reference/cwinapp-class.md#run), como se muestra a continuación:

[!code-cpp[NVC_MFCDocView#6](../mfc/codesnippet/cpp/special-cwinapp-services_1.cpp)]

Si no se suprime el subproceso de GDI+ en segundo plano, los comandos DDE se pueden emitir prematuramente a la aplicación antes de que se haya creado la ventana principal. Los comandos DDE emitidos por el Shell se pueden anular prematuramente, lo que da lugar a mensajes de error.

##  <a name="_core_file_manager_drag_and_drop"></a>Arrastrar y colocar del administrador de archivos

Los archivos se pueden arrastrar desde la ventana vista de archivos del administrador de archivos o el explorador de archivos a una ventana de la aplicación. Puede, por ejemplo, permitir que uno o varios archivos se arrastren a la ventana principal de una aplicación MDI, donde la aplicación podría recuperar los nombres de archivo y abrir las ventanas secundarias MDI para esos archivos.

Para habilitar arrastrar y colocar archivos en la aplicación, el Asistente para aplicaciones MFC escribe una llamada a la función miembro de [CWnd](../mfc/reference/cwnd-class.md) [DragAcceptFiles](../mfc/reference/cwnd-class.md#dragacceptfiles) para la ventana de marco principal en el `InitInstance`. Puede quitar esa llamada si no desea implementar la característica de arrastrar y colocar.

> [!NOTE]
>  También puede implementar capacidades de arrastrar y colocar más generales (arrastrando datos entre documentos o dentro de ellos) con OLE. Para obtener más información, vea el artículo [arrastrar y colocar de OLE](../mfc/drag-and-drop-ole.md).

##  <a name="_core_keeping_track_of_the_most_recently_used_documents"></a>Seguimiento de los documentos usados más recientemente

Cuando el usuario abre y cierra los archivos, el objeto de aplicación realiza un seguimiento de los cuatro archivos usados más recientemente. Los nombres de estos archivos se agregan al menú Archivo y se actualizan cuando cambian. El marco de trabajo almacena estos nombres de archivo en el registro o en el archivo. ini, con el mismo nombre que el proyecto y los Lee del archivo cuando se inicia la aplicación. El `InitInstance` invalidación que el Asistente para aplicaciones MFC crea para usted incluye una llamada a la función miembro [CWinApp](../mfc/reference/cwinapp-class.md) [LoadStdProfileSettings](../mfc/reference/cwinapp-class.md#loadstdprofilesettings), que carga información del registro o del archivo. ini, incluidos los nombres de archivo usados más recientemente.

Estas entradas se almacenan de la siguiente manera:

- En Windows NT, Windows 2000 y versiones posteriores, el valor se almacena en una clave del registro.

- En Windows 3. x, el valor se almacena en el archivo WIN. Archivo INI.

- En Windows 95 y versiones posteriores, el valor se almacena en una versión almacenada en caché de WIN. INI.

## <a name="see-also"></a>Consulte también

[CWinApp: la clase Application](../mfc/cwinapp-the-application-class.md)
