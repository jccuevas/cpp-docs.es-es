---
title: 'Windows Sockets: Usar la clase CAsyncSocket'
ms.date: 11/04/2016
helpviewer_keywords:
- CAsyncSocket class [MFC], programming model
- Windows Sockets [MFC], asynchronous
- sockets [MFC], converting between Unicode and MBCS strings
- SOCKET handle
- sockets [MFC], asynchronous operation
- Windows Sockets [MFC], converting Unicode and MBCS strings
ms.assetid: 825dae17-7c1b-4b86-8d6c-da7f1afb5d8d
ms.openlocfilehash: 3977308776c4ec6fed844038c4453ad03d065f98
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445944"
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows Sockets: Usar la clase CAsyncSocket

En este artículo se explica cómo usar la clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md). Tenga en cuenta que esta clase encapsula la API de Windows Sockets en un nivel muy bajo. `CAsyncSocket` es para su uso por parte de los programadores que conocen las comunicaciones de red en detalle pero desean la comodidad de las devoluciones de llamada para la notificación de eventos de red. En función de esta suposición, este artículo proporciona solo instrucciones básicas. Probablemente considere la posibilidad de usar `CAsyncSocket` si desea que Windows Sockets sea más fácil de tratar con varios protocolos de red en una aplicación MFC pero no desea sacrificar la flexibilidad. También podría sentir que puede obtener una mayor eficacia si programa las comunicaciones más directamente que con el modelo más general de `CSocket`de clase.

`CAsyncSocket` se documenta en la *referencia de MFC*. Visual C++ también proporciona la especificación de Windows Sockets, que se encuentra en la Windows SDK. Los detalles le quedan. Visual C++ no proporciona una aplicación de ejemplo para `CAsyncSocket`.

Si no tiene amplios conocimientos sobre las comunicaciones de red y desea una solución sencilla, use la clase [CSocket](../mfc/reference/csocket-class.md) con un objeto `CArchive`. Consulte [Windows Sockets: usar sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md) para obtener más información.

En este artículo se describe:

- Crear y usar un objeto de `CAsyncSocket`.

- [Sus responsabilidades con CAsyncSocket](#_core_your_responsibilities_with_casyncsocket).

##  <a name="_core_creating_and_using_a_casyncsocket_object"></a>Crear y usar un objeto CAsyncSocket

#### <a name="to-use-casyncsocket"></a>Para usar CAsyncSocket

1. Construya un objeto [CAsyncSocket](../mfc/reference/casyncsocket-class.md) y utilice el objeto para crear el identificador de **socket** subyacente.

   La creación de un socket sigue el patrón de MFC de construcción en dos fases.

   Por ejemplo:

   [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]

     O bien

   [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]

   En el primer constructor anterior se crea un objeto `CAsyncSocket` en la pila. El segundo constructor crea un `CAsyncSocket` en el montón. La primera llamada [Create](../mfc/reference/casyncsocket-class.md#create) anterior usa los parámetros predeterminados para crear un socket de flujo. La segunda llamada a `Create` crea un socket de datagrama con un puerto y una dirección especificados. (Puede utilizar `Create` versión con cualquier método de construcción).

   Los parámetros para `Create` son:

   - Un "puerto": un entero corto.

      Para un socket de servidor, debe especificar un puerto. Para un socket de cliente, normalmente acepta el valor predeterminado de este parámetro, lo que permite a Windows Sockets seleccionar un puerto.

   - Un tipo de socket: **SOCK_STREAM** (valor predeterminado) o **SOCK_DGRAM**.

   - Una "dirección" de socket, como "ftp.microsoft.com" o "128.56.22.8".

      Esta es la dirección del Protocolo de Internet (IP) en la red. Probablemente se basará siempre en el valor predeterminado de este parámetro.

   Los términos "puerto" y "dirección de socket" se explican en [Windows Sockets: puertos y direcciones de socket](../mfc/windows-sockets-ports-and-socket-addresses.md).

1. Si el socket es un cliente, conecte el objeto de socket a un socket de servidor mediante [CAsyncSocket:: Connect](../mfc/reference/casyncsocket-class.md#connect).

     O bien

   Si el socket es un servidor, establezca el socket para empezar a escuchar (con [CAsyncSocket:: Listen](../mfc/reference/casyncsocket-class.md#listen)) para los intentos de conexión desde un cliente. Al recibir una solicitud de conexión, se acepta con [CAsyncSocket:: Accept](../mfc/reference/casyncsocket-class.md#accept).

   Después de aceptar una conexión, puede realizar tareas como la validación de contraseñas.

    > [!NOTE]
    >  La función miembro `Accept` toma una referencia a un nuevo objeto `CSocket` vacío como su parámetro. Debe construir este objeto antes de llamar a `Accept`. Si este objeto de socket sale del ámbito, la conexión se cierra. No llame a `Create` para este nuevo objeto de socket. Para obtener un ejemplo, vea el artículo [Windows Sockets: secuencia de operaciones](../mfc/windows-sockets-sequence-of-operations.md).

1. Realice comunicaciones con otros Sockets llamando a las funciones miembro del objeto `CAsyncSocket` que encapsulan las funciones de la API de Windows Sockets.

   Vea la especificación de Windows Sockets y la clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md) en la *referencia de MFC*.

1. Destruya el objeto de `CAsyncSocket`.

   Si creó el objeto de socket en la pila, se llama a su Destructor cuando la función contenedora sale del ámbito. Si creó el objeto socket en el montón mediante el operador **New** , es responsable de usar el operador **Delete** para destruir el objeto.

   El destructor llama a la función miembro [Close](../mfc/reference/casyncsocket-class.md#close) del objeto antes de destruir el objeto.

Para obtener un ejemplo de esta secuencia en el código (realmente para un objeto `CSocket`), vea [Windows Sockets: secuencia de operaciones](../mfc/windows-sockets-sequence-of-operations.md).

##  <a name="_core_your_responsibilities_with_casyncsocket"></a>Sus responsabilidades con CAsyncSocket

Cuando se crea un objeto de la clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md), el objeto encapsula un identificador de **socket** de Windows y proporciona operaciones en ese controlador. Al usar `CAsyncSocket`, debe tratar todos los problemas que pueda encontrar si usa la API directamente. Por ejemplo:

- Escenarios de "bloqueo".

- Diferencias de orden de bytes entre el envío y la recepción de máquinas.

- Conversión entre cadenas Unicode y juegos de caracteres multibyte (MBCS).

Para obtener definiciones de estos términos e información adicional, vea [Windows Sockets: bloqueo](../mfc/windows-sockets-blocking.md), [Windows Sockets: ordenación de bytes](../mfc/windows-sockets-byte-ordering.md), [Windows Sockets: convertir cadenas](../mfc/windows-sockets-converting-strings.md).

A pesar de estos problemas, la clase `CAsycnSocket` puede ser la opción adecuada si la aplicación requiere toda la flexibilidad y el control que puede obtener. Si no es así, considere la posibilidad de usar la `CSocket` de clase en su lugar. `CSocket` oculta una gran cantidad de detalles: bombea mensajes de Windows durante las llamadas de bloqueo y le proporciona acceso a `CArchive`, que administra las diferencias de orden de bytes y la conversión de cadenas automáticamente.

Para más información, consulte:

- [Windows Sockets: Nociones](../mfc/windows-sockets-background.md)

- [Windows Sockets: Sockets de flujos](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Sockets de datagramas](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Consulte también

[Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)
