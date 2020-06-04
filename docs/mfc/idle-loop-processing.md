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
ms.openlocfilehash: 9579d4bb8768b0227453af401d6fdc8a8bd482b4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376008"
---
# <a name="idle-loop-processing"></a>Procesamiento de bucles inactivos

Muchas aplicaciones realizan un procesamiento prolongado "en segundo plano". A veces, las consideraciones de rendimiento dictan el uso de multithreading para dicho trabajo. Los subprocesos implican una sobrecarga de desarrollo adicional, por lo que no se recomiendan para tareas simples como el trabajo en tiempo de inactividad que MFC realiza en la función [OnIdle.](../mfc/reference/cwinthread-class.md#onidle) Este artículo se centra en el procesamiento inactivo. Para obtener más información acerca de multithreading, vea [Temas de multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Algunos tipos de procesamiento en segundo plano se realizan correctamente durante intervalos que el usuario no está interactuando de otro modo con la aplicación. En una aplicación desarrollada para el sistema operativo Microsoft Windows, una aplicación puede realizar el procesamiento en tiempo de inactividad dividiendo un proceso largo en muchos fragmentos pequeños. Después de procesar cada fragmento, la aplicación produce el control de ejecución en Windows mediante un bucle [PeekMessage.](/windows/win32/api/winuser/nf-winuser-peekmessagew)

En este artículo se explican dos formas de realizar el procesamiento inactivo en la aplicación:

- Uso de **PeekMessage** en el bucle de mensajes principal de MFC.

- Incrustar otro bucle **PeekMessage** en otro lugar de la aplicación.

## <a name="peekmessage-in-the-mfc-message-loop"></a><a name="_core_peekmessage_in_the_mfc_message_loop"></a>PeekMessage en el bucle de mensajes MFC

En una aplicación desarrollada con MFC, `CWinThread` el bucle de mensajes principal de la clase contiene un bucle de mensajes que llama a la API [PeekMessage](/windows/win32/api/winuser/nf-winuser-peekmessagew) Win32. Este bucle también `OnIdle` llama `CWinThread` a la función miembro de entre mensajes. Una aplicación puede procesar mensajes en este `OnIdle` tiempo de inactividad reemplazando la función.

> [!NOTE]
> `Run`, `OnIdle`y algunas otras funciones `CWinThread` miembro ahora `CWinApp`son miembros de clase en lugar de clase . La clase `CWinApp` se deriva de la clase `CWinThread`.

Para obtener más información acerca de cómo realizar el procesamiento inactivo, vea [OnIdle](../mfc/reference/cwinthread-class.md#onidle) en la *referencia de MFC*.

## <a name="peekmessage-elsewhere-in-your-application"></a><a name="_core_peekmessage_elsewhere_in_your_application"></a>PeekMessage en otra parte de su aplicación

Otro método para realizar el procesamiento inactivo en una aplicación implica incrustar un bucle de mensajes en una de las funciones. Este bucle de mensajes es muy similar al bucle de mensajes principal de MFC, que se encuentra en [CWinThread::Run](../mfc/reference/cwinthread-class.md#run). Esto significa que un bucle de este tipo en una aplicación desarrollada con MFC debe realizar muchas de las mismas funciones que el bucle de mensajes principal. En el fragmento de código siguiente se muestra cómo escribir un bucle de mensajes compatible con MFC:

[!code-cpp[NVC_MFCDocView#8](../mfc/codesnippet/cpp/idle-loop-processing_1.cpp)]

Este código, incrustado en una función, se repite siempre y cuando haya que realizar un procesamiento inactivo. Dentro de ese bucle, un `PeekMessage`bucle anidado llama repetidamente . Siempre que esa llamada devuelva un `CWinThread::PumpMessage` valor distinto de cero, el bucle llama para realizar la traducción y distribución normales de mensajes. Aunque `PumpMessage` no está documentado, puede examinar su código fuente en el archivo ThrdCore.Cpp en el directorio .

Una vez que finaliza el bucle interno, el bucle `OnIdle`externo realiza el procesamiento inactivo con una o más llamadas a . La primera llamada es para los propósitos de MFC. Puede realizar llamadas `OnIdle` adicionales para realizar su propio trabajo en segundo plano.

Para obtener más información acerca de cómo realizar el procesamiento inactivo, vea [OnIdle](../mfc/reference/cwinthread-class.md#onidle) en la referencia de la biblioteca MFC.

## <a name="see-also"></a>Consulte también

[Temas generales de MFC](../mfc/general-mfc-topics.md)
