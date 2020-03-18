---
title: 'CWinApp: The Application (Clase)'
ms.date: 11/04/2016
helpviewer_keywords:
- application class [MFC]
- CWinApp class [MFC], CWinThread
- MFC, WinMain and
- CWinApp class [MFC], multithreading
- CWinThread class [MFC], and CWinApp
- InitApplication method [MFC]
- WinMain method [MFC]
- WinMain method [MFC], in MFC
- CWinApp class [MFC], WinMain
ms.assetid: 935822bb-d463-481b-a5f6-9719d68ed1d5
ms.openlocfilehash: 8518e21a9fa6bcf5ac640cff25b17c5028046b06
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447024"
---
# <a name="cwinapp-the-application-class"></a>CWinApp: The Application (Clase)

La clase de aplicación principal de MFC encapsula la inicialización, ejecución y finalización de una aplicación para el sistema operativo Windows. Una aplicación compilada en el marco de trabajo debe tener solo un objeto de una clase derivada de [CWinApp](../mfc/reference/cwinapp-class.md). Este objeto se crea antes de crear Windows.

`CWinApp` se deriva de `CWinThread`, que representa el subproceso principal de ejecución de la aplicación, que puede tener uno o más subprocesos. En las versiones recientes de MFC, las funciones miembro `InitInstance`, **Run**, `ExitInstance`y `OnIdle` están realmente en `CWinThread`de clase. Estas funciones se tratan aquí como si fueran `CWinApp` miembros en su lugar, porque la discusión se refiere al rol del objeto como objeto de aplicación en lugar de como subproceso principal.

> [!NOTE]
>  La clase de aplicación constituye el subproceso de ejecución principal de la aplicación. Con las funciones de la API Win32, también puede crear subprocesos secundarios de ejecución. Estos subprocesos pueden utilizar la biblioteca MFC. Para obtener más información, vea [multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Al igual que cualquier programa del sistema operativo Windows, la aplicación de marco tiene una función `WinMain`. Sin embargo, en una aplicación de marco de trabajo, no se escribe `WinMain`. Lo proporciona la biblioteca de clases y se llama cuando se inicia la aplicación. `WinMain` realiza servicios estándar como el registro de clases de ventana. A continuación, llama a las funciones miembro del objeto de aplicación para inicializar y ejecutar la aplicación. (Puede personalizar `WinMain` invalidando las funciones miembro de `CWinApp` que `WinMain` llamadas).

Para inicializar la aplicación, `WinMain` llama a las funciones miembro `InitApplication` y `InitInstance` del objeto de la aplicación. Para ejecutar el bucle de mensajes de la aplicación, `WinMain` llama a la función miembro **Run** . Al finalizar, `WinMain` llama a la función miembro de `ExitInstance` del objeto de la aplicación.

> [!NOTE]
>  Los nombres que se muestran en **negrita** en esta documentación indican los elementos proporcionados C++por el biblioteca MFC y el elemento visual. Los nombres que se muestran en `monospaced` tipo indican los elementos que se crean o invalidan.

## <a name="see-also"></a>Consulte también

[Temas generales de MFC](../mfc/general-mfc-topics.md)<br/>
[CWinApp y el Asistente para aplicaciones MFC](../mfc/cwinapp-and-the-mfc-application-wizard.md)<br/>
[Funciones miembro de CWinApp que se pueden sobrecargar](../mfc/overridable-cwinapp-member-functions.md)<br/>
[Servicios especiales de CWinApp](../mfc/special-cwinapp-services.md)
