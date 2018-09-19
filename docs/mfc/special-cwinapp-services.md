---
title: Servicios especiales de CWinApp | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- LoadStdProfileSettings
- EnableShellOpen
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: beac10db09fefdf38d8e038855eb62ba8af80dbe
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218617"
---
# <a name="special-cwinapp-services"></a>Servicios especiales de CWinApp
Además de ejecutar el bucle de mensajes y darle la oportunidad de inicializar la aplicación y limpiar después de ella, [CWinApp](../mfc/reference/cwinapp-class.md) proporciona otros servicios.  
  
##  <a name="_core_shell_registration"></a> Registro Shell  
 De forma predeterminada, el Asistente para aplicaciones MFC permite al usuario que abra los archivos de datos que ha creado la aplicación haciendo doble clic en ellos en el Explorador de archivos o el Administrador de archivos. Si la aplicación es una aplicación MDI y especifica una extensión para los archivos que crea la aplicación, el Asistente para aplicaciones MFC agrega las llamadas a la [RegisterShellFileTypes](../mfc/reference/cwinapp-class.md#registershellfiletypes) y [EnableShellOpen](../mfc/reference/cwinapp-class.md#enableshellopen)las funciones miembro de [CWinApp](../mfc/reference/cwinapp-class.md) a la `InitInstance` invalidación que escribe para usted.  
  
 `RegisterShellFileTypes` tipos de documento de la aplicación se registra con el Explorador de archivos o el Administrador de archivos. La función agrega entradas a la base de datos de registro que mantiene Windows. Las entradas de registrar cada tipo de documento, asociación una extensión de archivo con el tipo de archivo, especifican una línea de comandos para abrir la aplicación y especifican un comando de datos dinámicos DDE (intercambio) para abrir un documento de ese tipo.  
  
 `EnableShellOpen` completa el proceso al permitir que la aplicación recibir comandos DDE de explorador de archivos o el Administrador de archivos para abrir el archivo elegido por el usuario.  
  
 Esta compatibilidad de registro automático en `CWinApp` elimina la necesidad de incluir un archivo .reg con la aplicación o para realizar el trabajo de instalación especial.  
  
 Si desea inicializar GDI + para la aplicación (mediante una llamada a [GdiplusStartup](/windows/desktop/api/gdiplusinit/nf-gdiplusinit-gdiplusstartup) en su [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) función), tendrá que suprimir el subproceso en segundo plano GDI +.  
  
 Puede hacerlo estableciendo la `SuppressBackgroundThread` miembro de la [GdiplusStartupInput](/windows/desktop/api/gdiplusinit/ns-gdiplusinit-gdiplusstartupinput) estructura **TRUE**. Al suprimir GDI + en segundo plano el subproceso, el `NotificationHook` y `NotificationUnhook` deben realizarse llamadas inmediatamente anteriores a entran y salen de bucle de mensajes de la aplicación. Para obtener más información sobre estas llamadas, vea [GdiplusStartupOutput](/windows/desktop/api/gdiplusinit/ns-gdiplusinit-gdiplusstartupoutput). Por lo tanto, un buen lugar para llamar a `GdiplusStartup` y las funciones de notificación de enlace debería estar en un reemplazo de la función virtual [CWinApp:: Run](../mfc/reference/cwinapp-class.md#run), tal y como se muestra a continuación:  
  
 [!code-cpp[NVC_MFCDocView#6](../mfc/codesnippet/cpp/special-cwinapp-services_1.cpp)]  
  
 Si no se suprima el fondo subproceso GDI +, comandos DDE pueden emitirse antes de tiempo a la aplicación antes de que se ha creado su ventana principal. Los comandos DDE emitidos por el shell pueden ser anula prematuramente, los mensajes de error.  
  
##  <a name="_core_file_manager_drag_and_drop"></a> Administrador de archivos de arrastrar y colocar  
 Los archivos se pueden arrastrar desde la ventana de vista de archivo en el Administrador de archivos o el Explorador de archivos a una ventana de la aplicación. Por ejemplo, podría habilitar uno o varios archivos para que se pueden arrastrar a la ventana principal de una aplicación MDI, donde la aplicación puede recuperar los nombres de archivo y abrir ventanas secundarias MDI para esos archivos.  
  
 Para habilitar el archivo arrastrar y colocar en la aplicación, el Asistente para aplicaciones MFC escribe una llamada a la [CWnd](../mfc/reference/cwnd-class.md) función miembro [DragAcceptFiles](../mfc/reference/cwnd-class.md#dragacceptfiles) de la ventana de marco principal en su `InitInstance`. Puede quitar esa llamada si no desea implementar la característica de arrastrar y colocar.  
  
> [!NOTE]
>  También puede implementar capacidades de arrastrar y colocar más generales, arrastrar datos entre o dentro de documentos, con OLE. Para obtener información, consulte el artículo [arrastrar y colocar (OLE)](../mfc/drag-and-drop-ole.md).  
  
##  <a name="_core_keeping_track_of_the_most_recently_used_documents"></a> Realizar el seguimiento de más documentos usados recientemente  
 Cuando el usuario abre y cierra archivos, el objeto de aplicación realiza un seguimiento de los cuatro archivos usados más recientemente. Los nombres de estos archivos se agregan al menú archivo y se actualizan cuando cambian. El marco de trabajo almacena estos nombres de archivo en el registro o en el archivo. ini, con el mismo nombre que el proyecto y los lee desde el archivo cuando se inicia la aplicación. El `InitInstance` invalidar que el Asistente para aplicaciones MFC crea para incluye una llamada a la [CWinApp](../mfc/reference/cwinapp-class.md) función miembro [LoadStdProfileSettings](../mfc/reference/cwinapp-class.md#loadstdprofilesettings), que carga la información de registro o .ini archivo, incluyendo la utilizados más recientemente los nombres de archivo.  
  
 Estas entradas se almacenan como sigue:  
  
-   En Windows NT, Windows 2000 y versiones posteriores, el valor se almacena una clave del registro.  
  
-   En Windows 3.x, el valor se almacena en el archivo WIN. Archivo INI.  
  
-   En Windows 95 y versiones posteriores, el valor se almacena en una versión en caché de WIN. INI.  
  
## <a name="see-also"></a>Vea también  
 [CWinApp: la clase Application](../mfc/cwinapp-the-application-class.md)