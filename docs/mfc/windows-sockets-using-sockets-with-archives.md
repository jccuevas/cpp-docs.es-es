---
title: 'Windows Sockets: Usar Sockets con archivos'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], archives
- sockets [MFC], with archives
- archives [MFC], and Windows Sockets
- CSocket class [MFC], programming model
ms.assetid: 17e71a99-a09e-4e1a-9fda-13d62805c824
ms.openlocfilehash: 71a7ed1f1b67bed157805328679a18ceabf201d3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261510"
---
# <a name="windows-sockets-using-sockets-with-archives"></a>Windows Sockets: Usar Sockets con archivos

Este artículo se describe la [modelo de programación de CSocket](#_core_the_csocket_programming_model). Clase [CSocket](../mfc/reference/csocket-class.md) proporciona compatibilidad con el socket en un nivel superior de abstracción de clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md). `CSocket` usa una versión del protocolo de serialización de MFC para pasar datos hacia y desde un objeto de socket a través de un MFC [CArchive](../mfc/reference/carchive-class.md) objeto. `CSocket` proporciona el bloqueo (mientras administra el procesamiento en segundo plano de los mensajes de Windows) y proporciona acceso a `CArchive`, que administra muchos aspectos de la comunicación que tendría que hacer usted mismo mediante la API sin formato o la clase `CAsyncSocket`.

> [!TIP]
>  Puede usar la clase `CSocket` por sí mismo, como una versión más conveniente de `CAsyncSocket`, pero el modelo de programación más sencillo es usar `CSocket` con un `CArchive` objeto.

Para obtener más información sobre cómo funciona la implementación de los sockets con archivos, consulte [Windows Sockets: Cómo funcionan los Sockets con archivos](../mfc/windows-sockets-how-sockets-with-archives-work.md). Por ejemplo de código, consulte [Windows Sockets: Secuencia de operaciones](../mfc/windows-sockets-sequence-of-operations.md) y [Windows Sockets: Ejemplo de Sockets que usan archivos](../mfc/windows-sockets-example-of-sockets-using-archives.md). Para obtener información sobre algunas de las funciones que puede obtener al derivar sus propias clases de las clases de sockets, consulte [Windows Sockets: Derivación de clases de Socket](../mfc/windows-sockets-deriving-from-socket-classes.md).

> [!NOTE]
>  Si está escribiendo un programa de cliente MFC para comunicarse con servidores establecidos (no basados en MFC), no enviar los objetos de C++ a través del archivo. A menos que el servidor es una aplicación MFC que reconozca los tipos de objetos que desea enviar, no será capaz de recibir y deserializar los objetos. Para obtener material relacionado en el asunto de la comunicación con aplicaciones no basados en MFC, vea también el artículo [Windows Sockets: Orden de bytes](../mfc/windows-sockets-byte-ordering.md).

##  <a name="_core_the_csocket_programming_model"></a> El modelo de programación de CSocket

Mediante un `CSocket` objeto implica crear y asociar varios objetos de clase MFC. En el procedimiento general siguiente, se toma cada paso por el socket de servidor y el socket de cliente, excepto el paso 3, en el que cada tipo de socket requiere una acción diferente.

> [!TIP]
>  En tiempo de ejecución, la aplicación de servidor suele empezar por estar preparada y "escucha" cuando la aplicación cliente busca una conexión. Si el servidor no está listo cuando el cliente intenta conectarse, normalmente requieren la aplicación de usuario para intentar conectar de nuevo más tarde.

#### <a name="to-set-up-communication-between-a-server-socket-and-a-client-socket"></a>Para configurar la comunicación entre un socket de servidor y un socket de cliente

1. Construir un [CSocket](../mfc/reference/csocket-class.md) objeto.

1. El objeto usa para crear subyacente **SOCKET** controlar.

   Para un `CSocket` objeto de cliente, normalmente debe usar los parámetros predeterminados para [crear](../mfc/reference/casyncsocket-class.md#create), a menos que necesite un socket de datagrama. Para un `CSocket` objeto de servidor, debe especificar un puerto en el `Create` llamar.

    > [!NOTE]
    >  `CArchive` no funciona con sockets de datagramas. Si desea usar `CSocket` para un socket de datagrama, debe usar la clase como utilizaría `CAsyncSocket`, es decir, sin un archivo. Dado que los datagramas no son confiables (no garantiza que lleguen y puede repetirse o que vengan desordenados), no son compatibles con la serialización a través de un archivo. Esperar una operación de serialización para completar de forma confiable y en secuencia. Si intenta usar `CSocket` con un `CArchive` de objeto para un datagrama, se produce un error en una aserción de MFC.

1. Si el socket es un cliente, llame a [CAsyncSocket:: Connect](../mfc/reference/casyncsocket-class.md#connect) para conectar el objeto de socket a un socket de servidor.

     O bien

   Si el socket es un servidor, llame a [CAsyncSocket:: Listen](../mfc/reference/casyncsocket-class.md#listen) para empezar a escuchar los intentos de conexión desde un cliente. Al recibir una solicitud de conexión, aceptarla mediante una llamada a [CAsyncSocket:: Accept](../mfc/reference/casyncsocket-class.md#accept).

    > [!NOTE]
    >  El `Accept` función miembro toma una referencia a una nueva y vacía `CSocket` objeto como su parámetro. Debe construir este objeto antes de llamar a `Accept`. Si este objeto socket se sale del ámbito, se cierra la conexión. No llame a `Create` para este nuevo objeto de socket.

1. Crear un [CSocketFile](../mfc/reference/csocketfile-class.md) objeto, asociar el `CSocket` objeto con él.

1. Crear un [CArchive](../mfc/reference/carchive-class.md) objeto para cargar (recibir) o almacenamiento de datos (enviar). El archivo está asociado con el `CSocketFile` objeto.

   Tenga en cuenta que `CArchive` no funciona con sockets de datagramas.

1. Use la `CArchive` objeto para pasar datos entre los sockets de cliente y servidor.

   Tenga en cuenta que una determinada `CArchive` objeto mueve los datos en un solo sentido: para cargar (recibir) o almacenar (enviar). En algunos casos, usará dos `CArchive` objetos: uno para enviar datos, otro para recibir confirmaciones.

   Después de aceptar una conexión y configurar el archivo, puede realizar tareas como la validación de contraseñas.

1. Destruir el archivo, archivo de socket y objetos de socket.

    > [!NOTE]
    >  Clase `CArchive` proporciona el `IsBufferEmpty` función miembro específicamente para su uso con la clase `CSocket`. Por ejemplo, si el búfer contiene varios mensajes de datos, necesita un bucle hasta que todos ellos se leen y se borra el búfer. En caso contrario, la siguiente notificación de que hay datos para poder recibir podría retrasarse indefinidamente. Use `IsBufferEmpty` para garantizar que recuperar todos los datos.

El artículo [Windows Sockets: Secuencia de operaciones](../mfc/windows-sockets-sequence-of-operations.md) muestra ambos lados de este proceso con código de ejemplo.

Para obtener más información, consulte:

- [Windows Sockets: Sockets de Stream](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Sockets de datagrama](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Vea también

[Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CSocket::Create](../mfc/reference/csocket-class.md#create)
