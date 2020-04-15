---
title: 'Windows Sockets: Usar sockets con archivos'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], archives
- sockets [MFC], with archives
- archives [MFC], and Windows Sockets
- CSocket class [MFC], programming model
ms.assetid: 17e71a99-a09e-4e1a-9fda-13d62805c824
ms.openlocfilehash: 55b4f9a5412c1447fe2b3bde10cb934b91abf008
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359952"
---
# <a name="windows-sockets-using-sockets-with-archives"></a>Windows Sockets: Usar sockets con archivos

En este artículo se describe el modelo de [programación CSocket.](#_core_the_csocket_programming_model) La clase [CSocket](../mfc/reference/csocket-class.md) proporciona compatibilidad de socket en un nivel de abstracción superior al de la clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md). `CSocket`utiliza una versión del protocolo de serialización MFC para pasar datos a y desde un objeto de socket a través de un objeto [CArchive](../mfc/reference/carchive-class.md) de MFC. `CSocket`proporciona bloqueo (mientras se administra el procesamiento `CArchive`en segundo plano de los mensajes de Windows) y le da `CAsyncSocket`acceso a , que administra muchos aspectos de la comunicación que tendría que hacer usted mismo utilizando la API sin procesar o la clase.

> [!TIP]
> Puede utilizar `CSocket` la clase por sí mismo, como una versión más conveniente de `CAsyncSocket`, pero el modelo de programación más simple es utilizar `CSocket` con un `CArchive` objeto.

Para obtener más información sobre cómo funciona la implementación de sockets con archivos, vea [Windows Sockets: How Sockets with Archives Work](../mfc/windows-sockets-how-sockets-with-archives-work.md). Para obtener código de ejemplo, vea [Windows Sockets: Sequence of Operations](../mfc/windows-sockets-sequence-of-operations.md) and Windows [Sockets: Example of Sockets Using Archives](../mfc/windows-sockets-example-of-sockets-using-archives.md). Para obtener información sobre algunas de las funciones que puede obtener derivando sus propias clases de las clases de sockets, vea [Windows Sockets: Deriving from Socket Classes](../mfc/windows-sockets-deriving-from-socket-classes.md).

> [!NOTE]
> Si está escribiendo un programa cliente MFC para comunicarse con servidores establecidos (no MFC), no envíe objetos C++ a través del archivo. A menos que el servidor sea una aplicación MFC que comprenda los tipos de objetos que desea enviar, no podrá recibir y deserializar los objetos. Para obtener material relacionado sobre el tema de la comunicación con aplicaciones que no son MFC, vea también el artículo [Windows Sockets: Byte Ordering](../mfc/windows-sockets-byte-ordering.md).

## <a name="the-csocket-programming-model"></a><a name="_core_the_csocket_programming_model"></a>El modelo de programación CSocket

El `CSocket` uso de un objeto implica crear y asociar varios objetos de clase MFC. En el procedimiento general siguiente, cada paso lo realiza el socket de servidor y el socket de cliente, excepto el paso 3, en el que cada tipo de socket requiere una acción diferente.

> [!TIP]
> En tiempo de ejecución, la aplicación de servidor normalmente se inicia primero para estar lista y "escuchar" cuando la aplicación cliente busca una conexión. Si el servidor no está listo cuando el cliente intenta conectarse, normalmente necesita que la aplicación de usuario intente conectarse de nuevo más adelante.

#### <a name="to-set-up-communication-between-a-server-socket-and-a-client-socket"></a>Para configurar la comunicación entre un socket de servidor y un socket de cliente

1. Construir un [CSocket](../mfc/reference/csocket-class.md) objeto.

1. Utilice el objeto para crear el identificador **SOCKET** subyacente.

   Para `CSocket` un objeto de cliente, normalmente debe utilizar los parámetros predeterminados para [Crear](../mfc/reference/casyncsocket-class.md#create), a menos que necesite un socket de datagrama. Para `CSocket` un objeto de servidor, debe `Create` especificar un puerto en la llamada.

    > [!NOTE]
    >  `CArchive`no funciona con sockets de datagramas. Si desea utilizar `CSocket` para un socket de datagrama, debe `CAsyncSocket`utilizar la clase como usaría, es decir, sin un archivo. Dado que los datagramas no son fiables (no se garantiza que lleguen y pueden repetirse o estar fuera de secuencia), no son compatibles con la serialización a través de un archivo. Espera que una operación de serialización se complete de forma fiable y en secuencia. Si intenta usar `CSocket` con `CArchive` un objeto para un datagrama, se produce un error en una aserción MFC.

1. Si el socket es un cliente, llame a [CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect) para conectar el objeto de socket a un socket de servidor.

     o bien

   Si el socket es un servidor, llame a [CAsyncSocket::Listen](../mfc/reference/casyncsocket-class.md#listen) para comenzar a escuchar los intentos de conexión desde un cliente. Al recibir una solicitud de conexión, acéptela llamando a [CAsyncSocket::Accept](../mfc/reference/casyncsocket-class.md#accept).

    > [!NOTE]
    >  La `Accept` función miembro toma una `CSocket` referencia a un nuevo objeto vacío como parámetro. Debe construir este objeto `Accept`antes de llamar a . Si este objeto de socket sale del ámbito, la conexión se cierra. No llame `Create` a este nuevo objeto de socket.

1. Cree un [cSocketFile](../mfc/reference/csocketfile-class.md) objeto, `CSocket` asociando el objeto con él.

1. Cree un objeto [CArchive](../mfc/reference/carchive-class.md) para cargar (recibir) o almacenar (enviar) datos. El archivo está `CSocketFile` asociado al objeto.

   Tenga en `CArchive` cuenta que no funciona con sockets de datagramas.

1. Utilice `CArchive` el objeto para pasar datos entre los sockets de cliente y servidor.

   Tenga en cuenta `CArchive` que un objeto determinado mueve los datos en una sola dirección: ya sea para cargar (recibir) o almacenar (enviar). En algunos casos, utilizará `CArchive` dos objetos: uno para enviar datos y el otro para recibir confirmaciones.

   Después de aceptar una conexión y configurar el archivo, puede realizar tareas como validar contraseñas.

1. Destruye los objetos de archivo, archivo de socket y socket.

    > [!NOTE]
    >  Clase `CArchive` proporciona `IsBufferEmpty` la función miembro específicamente para su uso con la clase `CSocket`. Si el búfer contiene varios mensajes de datos, por ejemplo, debe realizar un bucle hasta que se lean todos ellos y se borre el búfer. De lo contrario, la siguiente notificación de que hay datos que se van a recibir puede retrasarse indefinidamente. Utilícelo `IsBufferEmpty` para asegurarse de recuperar todos los datos.

El artículo [Windows Sockets: Sequence of Operations](../mfc/windows-sockets-sequence-of-operations.md) ilustra ambos lados de este proceso con código de ejemplo.

Para más información, consulte:

- [Windows Sockets: Sockets de secuencias](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Sockets de datagramas](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Consulte también

[Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CSocket::Crear](../mfc/reference/csocket-class.md#create)
