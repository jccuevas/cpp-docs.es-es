---
title: 'Windows Sockets: Usar la clase CAsyncSocket'
ms.date: 11/04/2016
f1_keywords:
- CAsyncSocket
helpviewer_keywords:
- CAsyncSocket class [MFC], programming model
- Windows Sockets [MFC], asynchronous
- sockets [MFC], converting between Unicode and MBCS strings
- SOCKET handle
- sockets [MFC], asynchronous operation
- Windows Sockets [MFC], converting Unicode and MBCS strings
ms.assetid: 825dae17-7c1b-4b86-8d6c-da7f1afb5d8d
ms.openlocfilehash: 51274791393d95517bd8de5ae7248dc634018037
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263118"
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows Sockets: Usar la clase CAsyncSocket

En este artículo se explica cómo usar la clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md). Tenga en cuenta que esta clase encapsula la API de Windows Sockets en un nivel muy bajo. `CAsyncSocket` está destinado a los programadores que conoce las comunicaciones de red en detalle, pero desean la comodidad de devoluciones de llamada para recibir notificaciones de eventos de la red. Según esta suposición, este artículo proporciona sólo la instrucción básica. Probablemente se debe considerar el uso `CAsyncSocket` si desea la facilidad de Windows Sockets de trabajar con varios protocolos de red en una aplicación MFC, pero no desea sacrificar la flexibilidad. También podría notar que puede obtener una mayor eficacia al programar las comunicaciones más directamente por sí mismo, lo que podría mediante el modelo alternativo más general de clase `CSocket`.

`CAsyncSocket` se documenta en el *referencia de MFC*. Visual C++ también proporciona la especificación Windows Sockets, que se encuentra en el SDK de Windows. Los detalles se dejan a usted. Visual C++ no proporciona una aplicación de ejemplo para `CAsyncSocket`.

Si no tiene muchos conocimientos acerca de las comunicaciones de red y desea una solución sencilla, utilice la clase [CSocket](../mfc/reference/csocket-class.md) con un `CArchive` objeto. Consulte [Windows Sockets: Usar Sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md) para obtener más información.

En este artículo se tratan los aspectos siguientes:

- Crear y usar un `CAsyncSocket` objeto.

- [Sus responsabilidades con CAsyncSocket](#_core_your_responsibilities_with_casyncsocket).

##  <a name="_core_creating_and_using_a_casyncsocket_object"></a> Creación y uso de un objeto CAsyncSocket

#### <a name="to-use-casyncsocket"></a>Para utilizar CAsyncSocket

1. Construir un [CAsyncSocket](../mfc/reference/casyncsocket-class.md) de objeto y el objeto usa para crear subyacente **SOCKET** controlar.

   Creación de un socket sigue el patrón MFC de construcción en dos fases.

   Por ejemplo:

   [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]

     O bien

   [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]

   El primer constructor anterior crea un `CAsyncSocket` objeto en la pila. El segundo constructor crea un `CAsyncSocket` en el montón. La primera [crear](../mfc/reference/casyncsocket-class.md#create) llamada anterior utiliza los parámetros predeterminados para crear un socket de secuencia. El segundo `Create` llamada crea un socket de datagrama con un puerto especificado y la dirección. (Se puede usar `Create` versión con cualquiera de estos métodos de construcción.)

   Los parámetros de `Create` son:

   - Un "puerto": un entero corto.

         For a server socket, you must specify a port. For a client socket, you typically accept the default value for this parameter, which lets Windows Sockets select a port.

   - Un tipo de socket: **SOCK_STREAM** (valor predeterminado) o **SOCK_DGRAM**.

   - Un socket "address", como "ftp.microsoft.com" o "128.56.22.8".

         This is your Internet Protocol (IP) address on the network. You will probably always rely on the default value for this parameter.

   Se explica los términos "puerto" y "dirección de socket" en [Windows Sockets: Puertos y direcciones de Socket](../mfc/windows-sockets-ports-and-socket-addresses.md).

1. Si el socket es un cliente, conecte el objeto de socket a un servidor de socket, mediante [CAsyncSocket:: Connect](../mfc/reference/casyncsocket-class.md#connect).

     O bien

   Si el socket es un servidor, establecer el socket para empezar a escuchar (con [CAsyncSocket:: Listen](../mfc/reference/casyncsocket-class.md#listen)) de intentos de conexión desde un cliente. Al recibir una solicitud de conexión, aceptarla con [CAsyncSocket:: Accept](../mfc/reference/casyncsocket-class.md#accept).

   Después de aceptar una conexión, puede realizar tareas como la validación de contraseñas.

    > [!NOTE]
    >  El `Accept` función miembro toma una referencia a una nueva y vacía `CSocket` objeto como su parámetro. Debe construir este objeto antes de llamar a `Accept`. Si este objeto socket se sale del ámbito, se cierra la conexión. No llame a `Create` para este nuevo objeto de socket. Para obtener un ejemplo, consulte el artículo [Windows Sockets: Secuencia de operaciones](../mfc/windows-sockets-sequence-of-operations.md).

1. Llevar a cabo las comunicaciones con otros sockets mediante una llamada a la `CAsyncSocket` funciones de miembro del objeto que encapsulan las funciones de Windows Sockets API.

   Vea la especificación Windows Sockets y la clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md) en el *referencia de MFC*.

1. Destruir el `CAsyncSocket` objeto.

   Si ha creado el objeto de socket en la pila, su destructor se llama cuando la función contenedora se sale del ámbito. Si ha creado el objeto de socket en el montón, usando la **nueva** operador, usted es responsable de usar el **eliminar** operador para destruir el objeto.

   El destructor llama al método del objeto [cerrar](../mfc/reference/casyncsocket-class.md#close) función miembro antes de destruir el objeto.

Para obtener un ejemplo de esta secuencia de código (en realidad, para un `CSocket` objeto), consulte [Windows Sockets: Secuencia de operaciones](../mfc/windows-sockets-sequence-of-operations.md).

##  <a name="_core_your_responsibilities_with_casyncsocket"></a> Sus responsabilidades con CAsyncSocket

Cuando se crea un objeto de clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md), encapsula el objeto de un Windows **SOCKET** controlar y proporciona las operaciones en ese controlador. Cuando usas `CAsyncSocket`, debe tratar con todos los problemas que puede enfrentarse si utiliza la API directamente. Por ejemplo:

- Escenarios de "Bloqueo".

- Diferencias entre el envío y recepción de las máquinas del orden de bytes.

- Convertir entre Unicode y juegos de caracteres multibyte conjunto de cadenas (MBCS).

Para obtener definiciones de estos términos y obtener más información, vea [Windows Sockets: Bloqueo](../mfc/windows-sockets-blocking.md), [Windows Sockets: Orden de bytes](../mfc/windows-sockets-byte-ordering.md), [Windows Sockets: Convertir cadenas](../mfc/windows-sockets-converting-strings.md).

A pesar de estos problemas, clase `CAsycnSocket` puede ser la opción más adecuada para usted si la aplicación requiere toda la flexibilidad y control que se puede obtener. Si no, debe considerar el uso de la clase `CSocket` en su lugar. `CSocket` oculta una gran cantidad de detalles: TI bombea mensajes durante llamadas de bloqueo de Windows y le proporciona acceso a `CArchive`, que administra las diferencias de orden de bytes y la conversión de cadenas.

Para obtener más información, consulte:

- [Windows Sockets: En segundo plano](../mfc/windows-sockets-background.md)

- [Windows Sockets: Sockets de Stream](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Sockets de datagrama](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Vea también

[Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)
