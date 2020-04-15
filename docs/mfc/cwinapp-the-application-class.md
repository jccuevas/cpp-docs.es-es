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
ms.openlocfilehash: 007a4e53fd9b3eae612947cd76ee352776572d4f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373523"
---
# <a name="cwinapp-the-application-class"></a>CWinApp: The Application (Clase)

La clase de aplicación principal de MFC encapsula la inicialización, ejecución y terminación de una aplicación para el sistema operativo Windows. Una aplicación compilada en el marco de trabajo debe tener un único objeto de una clase derivada de [CWinApp](../mfc/reference/cwinapp-class.md). Este objeto se construye antes de crear ventanas.

`CWinApp`se deriva `CWinThread`de , que representa el subproceso principal de ejecución de la aplicación, que podría tener uno o varios subprocesos. En versiones recientes `InitInstance`de MFC, `OnIdle` las funciones miembro `CWinThread`, **Run**, `ExitInstance`y , están realmente en la clase . Estas funciones se describen `CWinApp` aquí como si fueran miembros en su lugar, porque la discusión se refiere al rol del objeto como objeto de aplicación en lugar de como subproceso principal.

> [!NOTE]
> La clase de aplicación constituye el subproceso principal de ejecución de la aplicación. Con las funciones de la API de Win32, también puede crear subprocesos secundarios de ejecución. Estos subprocesos pueden usar la biblioteca MFC. Para obtener más información, consulte [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Al igual que cualquier programa para el `WinMain` sistema operativo Windows, la aplicación marco de trabajo tiene una función. En una aplicación de marco de `WinMain`trabajo, sin embargo, no se escribe . Se proporciona por la biblioteca de clases y se llama cuando se inicia la aplicación. `WinMain`realiza servicios estándar como el registro de clases de ventana. A continuación, llama a las funciones miembro del objeto de aplicación para inicializar y ejecutar la aplicación. (Puede personalizar `WinMain` reemplazando `CWinApp` las funciones miembro que `WinMain` llama.)

Para inicializar la `WinMain` aplicación, llama `InitApplication` a `InitInstance` las funciones miembro y del objeto de aplicación. Para ejecutar el bucle de `WinMain` mensajes de la aplicación, llama a la **run** función miembro. Al finalizar, `WinMain` llama a `ExitInstance` la función miembro del objeto de aplicación.

> [!NOTE]
> Los nombres que se muestran en **negrita** en esta documentación indican los elementos proporcionados por Microsoft Foundation Class Library y Visual C++. Los nombres `monospaced` que se muestran en tipo indican los elementos que se crean o invalidan.

## <a name="see-also"></a>Consulte también

[Temas generales de MFC](../mfc/general-mfc-topics.md)<br/>
[CWinApp y el Asistente para aplicaciones MFC](../mfc/cwinapp-and-the-mfc-application-wizard.md)<br/>
[Funciones miembro de CWinApp que se pueden sobrecargar](../mfc/overridable-cwinapp-member-functions.md)<br/>
[Servicios especiales de CWinApp](../mfc/special-cwinapp-services.md)
