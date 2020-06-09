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
ms.openlocfilehash: 74ca89d91cf4e60b09a063551b526f177caed161
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624513"
---
# <a name="idle-loop-processing"></a>Procesamiento de bucles inactivos

Muchas aplicaciones realizan un procesamiento largo "en segundo plano". A veces, las consideraciones de rendimiento determinan el uso de multithreading para este tipo de trabajo. Los subprocesos implican una sobrecarga de desarrollo adicional, por lo que no se recomiendan para tareas sencillas como el trabajo en tiempo de inactividad que MFC hace en la función [OnIdle](reference/cwinthread-class.md#onidle) . Este artículo se centra en el procesamiento inactivo. Para obtener más información acerca del multithreading, vea [temas de multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Algunos tipos de procesamiento en segundo plano se realizan correctamente durante los intervalos en los que el usuario no está interactuando con la aplicación. En una aplicación desarrollada para el sistema operativo Microsoft Windows, una aplicación puede realizar el procesamiento en tiempo de inactividad dividiendo un proceso largo en muchos fragmentos pequeños. Después de procesar cada fragmento, la aplicación produce un control de ejecución en Windows mediante un bucle [PeekMessage](/windows/win32/api/winuser/nf-winuser-peekmessagew) .

En este artículo se explican dos maneras de realizar el procesamiento inactivo en la aplicación:

- Usar **PeekMessage** en el bucle de mensajes principal de MFC.

- Incrustar otro bucle **PeekMessage** en otra parte de la aplicación.

## <a name="peekmessage-in-the-mfc-message-loop"></a><a name="_core_peekmessage_in_the_mfc_message_loop"></a>PeekMessage en el bucle de mensajes de MFC

En una aplicación desarrollada con MFC, el bucle de mensajes principal de la `CWinThread` clase contiene un bucle de mensajes que llama a la API de Win32 [PeekMessage](/windows/win32/api/winuser/nf-winuser-peekmessagew) . Este bucle también llama a la `OnIdle` función miembro `CWinThread` entre los mensajes. Una aplicación puede procesar mensajes en este tiempo de inactividad invalidando la `OnIdle` función.

> [!NOTE]
> `Run`, `OnIdle` y algunas otras funciones miembro son ahora miembros de la clase `CWinThread` en lugar de la clase `CWinApp` . La clase `CWinApp` se deriva de la clase `CWinThread`.

Para obtener más información sobre cómo realizar el procesamiento [inactivo, vea OnIdle](reference/cwinthread-class.md#onidle) en la *referencia de MFC*.

## <a name="peekmessage-elsewhere-in-your-application"></a><a name="_core_peekmessage_elsewhere_in_your_application"></a>PeekMessage en otra parte de la aplicación

Otro método para realizar el procesamiento inactivo en una aplicación implica la incrustación de un bucle de mensajes en una de las funciones. Este bucle de mensajes es muy similar al bucle de mensajes principal de MFC, que se encuentra en [CWinThread:: Run](reference/cwinthread-class.md#run). Esto significa que este tipo de bucle en una aplicación desarrollada con MFC debe realizar muchas de las mismas funciones que el bucle de mensajes principal. En el fragmento de código siguiente se muestra cómo escribir un bucle de mensajes compatible con MFC:

[!code-cpp[NVC_MFCDocView#8](codesnippet/cpp/idle-loop-processing_1.cpp)]

Este código, incrustado en una función, se repite siempre que se produzca un procesamiento inactivo. Dentro de ese bucle, un bucle anidado llama repetidamente a `PeekMessage` . Siempre y cuando esa llamada devuelva un valor distinto de cero, el bucle llama `CWinThread::PumpMessage` a para realizar la traducción normal de mensajes y el envío. Aunque `PumpMessage` no esté documentado, puede examinar su código fuente en el archivo ThrdCore. cpp en el directorio \atlmfc\src\mfc de la instalación de Visual C++.

Una vez que finaliza el bucle interno, el bucle externo realiza el procesamiento inactivo con una o más llamadas a `OnIdle` . La primera llamada es para los propósitos de MFC. Puede realizar llamadas adicionales a `OnIdle` para realizar su propio trabajo en segundo plano.

Para obtener más información sobre cómo realizar el procesamiento [inactivo, vea OnIdle](reference/cwinthread-class.md#onidle) en la referencia de la biblioteca MFC.

## <a name="see-also"></a>Consulte también

[Temas generales de MFC](general-mfc-topics.md)
