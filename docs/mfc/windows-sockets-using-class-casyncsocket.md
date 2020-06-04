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
ms.openlocfilehash: d3fc32d9da54d9cf8c79e9e5de45b81c2ef64a6e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371968"
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows Sockets: Usar la clase CAsyncSocket

En este artículo se explica cómo utilizar la clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md). Tenga en cuenta que esta clase encapsula la API de Windows Sockets en un nivel muy bajo. `CAsyncSocket`es para ser utilizado por los programadores que conocen las comunicaciones de red en detalle, pero quieren la comodidad de las devoluciones de llamada para la notificación de eventos de red. Basándose en esta suposición, este artículo solo proporciona instrucciones básicas. Probablemente debería considerar `CAsyncSocket` el uso de si desea que Windows Sockets sea fácil de tratar con varios protocolos de red en una aplicación MFC, pero no desea sacrificar la flexibilidad. También puede sentir que puede obtener una mejor eficiencia mediante la programación de las `CSocket`comunicaciones más directamente usted mismo de lo que podría utilizando el modelo alternativo más general de la clase.

`CAsyncSocket`se documenta en la *Referencia de MFC*. Visual C++ también proporciona la especificación de Windows Sockets, que se encuentra en el Windows SDK. Los detalles se dejan a usted. Visual C++ no proporciona una `CAsyncSocket`aplicación de ejemplo para .

Si no tiene muy conocimiento sobre las comunicaciones de red y `CArchive` desea una solución sencilla, utilice la clase [CSocket](../mfc/reference/csocket-class.md) con un objeto. Consulte [Windows Sockets: Uso de sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md) para obtener más información.

En este artículo se describe:

- Creación y `CAsyncSocket` uso de un objeto.

- [Sus responsabilidades con CAsyncSocket](#_core_your_responsibilities_with_casyncsocket).

## <a name="creating-and-using-a-casyncsocket-object"></a><a name="_core_creating_and_using_a_casyncsocket_object"></a>Creación y uso de un objeto CAsyncSocket

#### <a name="to-use-casyncsocket"></a>Para usar CAsyncSocket

1. Construir un [CAsyncSocket](../mfc/reference/casyncsocket-class.md) objeto y utilizar el objeto para crear el identificador **SOCKET** subyacente.

   La creación de un socket sigue el patrón MFC de la construcción en dos etapas.

   Por ejemplo:

   [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]

     o bien

   [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]

   El primer constructor `CAsyncSocket` anterior crea un objeto en la pila. El segundo constructor `CAsyncSocket` crea un en el montón. La primera llamada [Create](../mfc/reference/casyncsocket-class.md#create) anterior utiliza los parámetros predeterminados para crear un socket de secuencia. La `Create` segunda llamada crea un socket de datagrama con un puerto y una dirección especificados. (Puede utilizar `Create` cualquiera de las versiones con cualquiera de los métodos de construcción.)

   Los parámetros a `Create` ser:

   - Un "puerto": un entero corto.

      Para un socket de servidor, debe especificar un puerto. Para un socket de cliente, normalmente se acepta el valor predeterminado para este parámetro, lo que permite a Windows Sockets seleccionar un puerto.

   - Un tipo de socket: **SOCK_STREAM** (valor predeterminado) o **SOCK_DGRAM**.

   - Un socket "dirección", como "ftp.microsoft.com" o "128.56.22.8".

      Esta es su dirección de protocolo de Internet (IP) en la red. Probablemente siempre confiará en el valor predeterminado para este parámetro.

   Los términos "puerto" y "dirección de socket" se explican en [Windows Sockets: Ports and Socket Addresses](../mfc/windows-sockets-ports-and-socket-addresses.md).

1. Si el socket es un cliente, conecte el objeto de socket a un socket de servidor mediante [CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect).

     o bien

   Si el socket es un servidor, establezca el socket para que comience a escuchar (con [CAsyncSocket::Listen](../mfc/reference/casyncsocket-class.md#listen)) para los intentos de conexión desde un cliente. Al recibir una solicitud de conexión, acéptela con [CAsyncSocket::Accept](../mfc/reference/casyncsocket-class.md#accept).

   Después de aceptar una conexión, puede realizar tareas como validar contraseñas.

    > [!NOTE]
    >  La `Accept` función miembro toma una `CSocket` referencia a un nuevo objeto vacío como parámetro. Debe construir este objeto `Accept`antes de llamar a . Si este objeto de socket sale del ámbito, la conexión se cierra. No llame `Create` a este nuevo objeto de socket. Para obtener un ejemplo, vea el artículo [Windows Sockets: Sequence of Operations](../mfc/windows-sockets-sequence-of-operations.md).

1. Llevar a cabo las comunicaciones con otros sockets mediante una llamada a las `CAsyncSocket` funciones miembro del objeto que encapsulan las funciones de la API de Windows Sockets.

   Consulte la especificación de Windows Sockets y la clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md) en la *referencia de MFC*.

1. Destruye `CAsyncSocket` el objeto.

   Si ha creado el objeto de socket en la pila, se llama a su destructor cuando la función contenedora sale del ámbito. Si ha creado el objeto de socket en el montón, utilizando el **operador new,** es responsable de utilizar el operador **delete** para destruir el objeto.

   El destructor llama a la función miembro [Close](../mfc/reference/casyncsocket-class.md#close) del objeto antes de destruir el objeto.

Para obtener un ejemplo de esta `CSocket` secuencia en código (en realidad para un objeto), vea [Windows Sockets: Sequence of Operations](../mfc/windows-sockets-sequence-of-operations.md).

## <a name="your-responsibilities-with-casyncsocket"></a><a name="_core_your_responsibilities_with_casyncsocket"></a>Sus responsabilidades con CAsyncSocket

Cuando se crea un objeto de la clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md), el objeto encapsula un identificador **SOCKET** de Windows y proporciona operaciones en ese identificador. Cuando utilice `CAsyncSocket`, debe tratar con todos los problemas que podría enfrentar si usa la API directamente. Por ejemplo:

- Escenarios de "bloqueo".

- Diferencias de orden de bytes entre las máquinas de envío y recepción.

- Conversión entre cadenas Unicode y de conjunto de caracteres multibyte (MBCS).

Para obtener definiciones de estos términos e información adicional, vea [Windows Sockets: Blocking](../mfc/windows-sockets-blocking.md), [Windows Sockets: Byte Ordering](../mfc/windows-sockets-byte-ordering.md), Windows [Sockets: Converting Strings](../mfc/windows-sockets-converting-strings.md).

A pesar de `CAsycnSocket` estos problemas, la clase puede ser la opción correcta para usted si su aplicación requiere toda la flexibilidad y el control que puede obtener. Si no es así, `CSocket` debería considerar el uso de la clase en su lugar. `CSocket`oculta muchos detalles de usted: bombea mensajes de Windows durante `CArchive`el bloqueo de llamadas y le da acceso a , que administra las diferencias de orden de bytes y la conversión de cadenas para usted.

Para más información, consulte:

- [Windows Sockets: Nociones](../mfc/windows-sockets-background.md)

- [Windows Sockets: Sockets de secuencias](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Sockets de datagramas](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Consulte también

[Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)
