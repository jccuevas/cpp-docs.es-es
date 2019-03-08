---
title: Procesamiento de bucles inactivos
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, background processing
- PeekMessage method [MFC], elsewhere than message loop
- PeekMessage method [MFC]
- MFC, messages
- messages [MFC], loops
- OnIdle method [MFC]
- processing [MFC], background
- idle loop processing [MFC]
- idle processing [MFC]
- threading [MFC], alternatives to multithreading
- processing, during idle loop
- processing [MFC]
- background processing [MFC]
ms.assetid: 5c7c46c1-6107-4304-895f-480983bb1e44
ms.openlocfilehash: 0d0e3fcba9ce447ec359958fc5ed59c6d596dd7a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287150"
---
# <a name="idle-loop-processing"></a>Procesamiento de bucles inactivos

Muchas aplicaciones realizan un procesamiento largo "en"segundo plano. A veces, las consideraciones de rendimiento exigir el uso de multithreading para dicho trabajo. Subprocesos implican una sobrecarga adicional de desarrollo, por lo que no se recomiendan para tareas sencillas, como el trabajo en tiempo de inactividad que realiza MFC en el [OnIdle](../mfc/reference/cwinthread-class.md#onidle) función. En este artículo se centra en el procesamiento en inactividad. Para obtener más información sobre multithreading, vea [temas de Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Algunos tipos de procesamiento en segundo plano ha terminado correctamente durante los intervalos que el usuario en caso contrario, no está interactuando con la aplicación. En una aplicación desarrollada para el sistema operativo Microsoft Windows, una aplicación puede realizar el procesamiento en tiempo de inactividad al dividir un proceso largo en muchos pequeños fragmentos. Después de procesar cada fragmento, la aplicación cede el control de ejecución para Windows usando una [PeekMessage](/windows/desktop/api/winuser/nf-winuser-peekmessagea) bucle.

En este artículo se explica dos formas de procesamiento en inactividad en la aplicación:

- Uso de **PeekMessage** en bucle de mensajes principal de MFC.

- Insertar otro **PeekMessage** bucle en otro lugar en la aplicación.

##  <a name="_core_peekmessage_in_the_mfc_message_loop"></a> PeekMessage en el bucle de mensajes MFC

En una aplicación desarrollada con MFC, un bucle principal del mensaje en el `CWinThread` clase contiene un bucle de mensajes que llama a la [PeekMessage](/windows/desktop/api/winuser/nf-winuser-peekmessagea) API Win32. Este bucle también llama a la `OnIdle` función miembro de `CWinThread` entre los mensajes. Una aplicación puede procesar los mensajes en este tiempo de inactividad invalidando el `OnIdle` función.

> [!NOTE]
>  `Run`, `OnIdle`, y otras funciones miembro son ahora miembros de clase `CWinThread` en lugar de la clase `CWinApp`. La clase `CWinApp` se deriva de la clase `CWinThread`.

Para obtener más información sobre el procesamiento en inactividad, consulte [OnIdle](../mfc/reference/cwinthread-class.md#onidle) en el *referencia de MFC*.

##  <a name="_core_peekmessage_elsewhere_in_your_application"></a> PeekMessage en otra parte de la aplicación

Otro método para llevar a cabo en una aplicación de procesamiento en inactividad implica insertar un bucle de mensajes en una de las funciones. Este bucle de mensajes es muy similar al bucle de mensajes principal de MFC, se encuentra en [CWinThread:: Run](../mfc/reference/cwinthread-class.md#run). Esto significa que un bucle en una aplicación desarrollada con MFC, debe realizar muchas de las mismas funciones que el bucle de mensajes principal. El fragmento de código siguiente muestra cómo escribir un bucle de mensajes que es compatible con MFC:

[!code-cpp[NVC_MFCDocView#8](../mfc/codesnippet/cpp/idle-loop-processing_1.cpp)]

Este código, incrustado en una función, bucles, siempre hay procesamiento en inactividad. Dentro de ese bucle, un bucle anidado llama repetidamente `PeekMessage`. Siempre que esa llamada devuelve un valor distinto de cero, el bucle llama `CWinThread::PumpMessage` para realizar la conversión de mensaje normal y envío. Aunque `PumpMessage` está documentado, puede examinar su código fuente en el archivo ThrdCore.Cpp en el directorio \atlmfc\src\mfc de la instalación de Visual C++.

Una vez que finaliza el bucle interno, el bucle externo realiza el procesamiento en inactividad con una o varias llamadas a `OnIdle`. La primera llamada es para fines de MFC. Puede realizar llamadas adicionales `OnIdle` para realizar su trabajo en segundo plano.

Para obtener más información sobre el procesamiento en inactividad, consulte [OnIdle](../mfc/reference/cwinthread-class.md#onidle) en la referencia de la biblioteca MFC.

## <a name="see-also"></a>Vea también

[Temas generales de MFC](../mfc/general-mfc-topics.md)
