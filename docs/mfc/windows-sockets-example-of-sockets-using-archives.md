---
title: 'Windows Sockets: Ejemplo de sockets que usan archivos'
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], with archives
- examples [MFC], Windows Sockets
- Windows Sockets [MFC], with archives
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
ms.openlocfilehash: 253a65430ae230fbc4deeb9bd5288f28237310d2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371089"
---
# <a name="windows-sockets-example-of-sockets-using-archives"></a>Windows Sockets: Ejemplo de sockets que usan archivos

En este artículo se presenta un ejemplo del uso de la clase [CSocket](../mfc/reference/csocket-class.md). El ejemplo `CArchive` emplea objetos para serializar datos a través de un socket. Tenga en cuenta que esto no es serialización de documentos hacia o desde un archivo.

En el ejemplo siguiente se muestra cómo se `CSocket` utiliza el archivo para enviar y recibir datos a través de objetos. El ejemplo está diseñado para que dos instancias de la aplicación (en el mismo equipo o en equipos diferentes de la red) intercambien datos. Una instancia envía datos, que la otra instancia recibe y reconoce. Cualquiera de las aplicaciones puede iniciar un intercambio y puede actuar como servidor o como cliente de la otra aplicación. La siguiente función se define en la clase de vista de la aplicación:

[!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/cpp/windows-sockets-example-of-sockets-using-archives_1.cpp)]

Lo más importante de este ejemplo es que su `Serialize` estructura es paralela a la de una función MFC. La `PacketSerialize` función miembro consta de una instrucción **if** con una cláusula **else.** La función recibe dos referencias [CArchive](../mfc/reference/carchive-class.md) como parámetros: *arData* y *arAck*. Si el objeto de archivo *arData* se establece para almacenar (enviar), se ejecuta la rama **if;** de lo contrario, si *arData* se establece para cargar (recibir) la función toma la rama **else.** Para obtener más información acerca de la serialización en MFC, vea [serialización](../mfc/how-to-make-a-type-safe-collection.md).

> [!NOTE]
> Se supone que el objeto de archivo *arAck* es lo opuesto a *arData*. Si *arData* es para enviar, *arAck* recibe y lo contrario es true.

Para el envío, la función de ejemplo se repite durante un número especificado de veces, cada vez generando algunos datos aleatorios para fines de demostración. La aplicación obtendría datos reales de algún origen, como un archivo. El operador de inserción**<<** del archivo *arData* ( ) se utiliza para enviar una secuencia de tres fragmentos consecutivos de datos:

- Un "encabezado" que especifica la naturaleza de los datos (en este caso, el valor de la variable *bValue* y cuántas copias se enviarán).

   Ambos elementos se generan aleatoriamente para este ejemplo.

- El número especificado de copias de los datos.

   El bucle **for** interno envía *bValue* el número especificado de veces.

- Cadena denominada *strText* que el receptor muestra a su usuario.

Para la recepción, la función funciona de forma similar,**>>** excepto que utiliza el operador de extracción del archivo ( ) para obtener datos del archivo. La aplicación receptora comprueba los datos que recibe, muestra el mensaje final "Recibido" y, a continuación, devuelve un mensaje que dice "Enviado" para que se muestre la aplicación de envío.

En este modelo de comunicaciones, la palabra "Recibido", el mensaje enviado en la variable *strText,* se muestra en el otro extremo de la comunicación, por lo que especifica al usuario receptor que se ha recibido un cierto número de paquetes de datos. El receptor responde con una cadena similar que dice "Enviado", para su visualización en la pantalla del remitente original. La recepción de ambas cadenas indica que se ha producido una comunicación correcta.

> [!CAUTION]
> Si está escribiendo un programa cliente MFC para comunicarse con servidores establecidos (no MFC), no envíe objetos C++ a través del archivo. A menos que el servidor sea una aplicación MFC que comprenda los tipos de objetos que desea enviar, no podrá recibir y deserializar los objetos. Un ejemplo del artículo [Windows Sockets: Byte Ordering](../mfc/windows-sockets-byte-ordering.md) muestra una comunicación de este tipo.

Para obtener más información, consulte Especificación de Windows Sockets: **htonl**, **htons**, **ntohl**, **ntohs**. Además, para obtener más información, consulte:

- [Windows Sockets: Derivar de las clases de socket](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets: Cómo funcionan los Sockets con archivos](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets: Nociones](../mfc/windows-sockets-background.md)

## <a name="see-also"></a>Consulte también

[Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CArchive::IsStoring](../mfc/reference/carchive-class.md#isstoring)<br/>
[CArchive::operador <<](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive::operador >>](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive::Flush](../mfc/reference/carchive-class.md#flush)<br/>
[CObject::Serialize](../mfc/reference/cobject-class.md#serialize)
