---
title: 'CWinApp: La clase Application'
ms.date: 11/04/2016
f1_keywords:
- CWinApp
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
ms.openlocfilehash: d9f0d4f5ba6b6b070b23ce98ecda8c7accf44934
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258715"
---
# <a name="cwinapp-the-application-class"></a>CWinApp: La clase Application

La clase principal de la aplicación de MFC encapsula la inicialización, la ejecución y la terminación de una aplicación para el sistema operativo de Windows. Una aplicación basada en el marco de trabajo debe tener uno y solo un objeto de una clase derivada de [CWinApp](../mfc/reference/cwinapp-class.md). Este objeto se construye antes de que windows se crean.

`CWinApp` se deriva de `CWinThread`, que representa el subproceso principal de ejecución de la aplicación, que puede tener uno o varios subprocesos. En versiones recientes de MFC, la `InitInstance`, **ejecutar**, `ExitInstance`, y `OnIdle` funciones miembro son realmente en la clase `CWinThread`. Estas funciones se tratan aquí como si fueran `CWinApp` miembros en su lugar, porque la discusión refiere al papel del objeto como objeto de aplicación en lugar de como subproceso principal.

> [!NOTE]
>  La clase de aplicación constituye el subproceso principal de la aplicación de ejecución. Usar funciones de la API de Win32, también puede crear subprocesos secundarios de ejecución. Estos subprocesos pueden usar la biblioteca MFC. Para obtener más información, consulte [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Al igual que cualquier programa para el sistema operativo de Windows, la aplicación de marco de trabajo tiene un `WinMain` función. En una aplicación de marco de trabajo, sin embargo, no se escriben `WinMain`. Proporcionado por la biblioteca de clases y se llama cuando se inicia la aplicación. `WinMain` lleva a cabo los servicios estándar, como registrar clases de ventana. A continuación, llama a funciones miembro del objeto de aplicación para inicializar y ejecutar la aplicación. (Se puede personalizar `WinMain` invalidando el `CWinApp` funciones miembro que `WinMain` llamadas.)

Para inicializar la aplicación, `WinMain` llama a su objeto de aplicación `InitApplication` y `InitInstance` funciones miembro. Para ejecutar el bucle de mensajes de la aplicación, `WinMain` llamadas la **ejecutar** función miembro. Al finalizar, `WinMain` llama al objeto de aplicación `ExitInstance` función miembro.

> [!NOTE]
>  Nombres que aparecen en **negrita** en esta documentación indicar elementos proporcionados por la biblioteca Microsoft Foundation Class y Visual C++. Nombres que aparecen en `monospaced` tipo indica los elementos que se crean o invalidar.

## <a name="see-also"></a>Vea también

[Temas generales de MFC](../mfc/general-mfc-topics.md)<br/>
[CWinApp y el Asistente para aplicaciones MFC](../mfc/cwinapp-and-the-mfc-application-wizard.md)<br/>
[Funciones miembro de CWinApp que se pueden sobrecargar](../mfc/overridable-cwinapp-member-functions.md)<br/>
[Servicios especiales de CWinApp](../mfc/special-cwinapp-services.md)
