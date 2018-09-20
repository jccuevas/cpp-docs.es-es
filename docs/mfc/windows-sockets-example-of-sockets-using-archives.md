---
title: 'Windows Sockets: Ejemplo de Sockets que usan archivos | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sockets [MFC], with archives
- examples [MFC], Windows Sockets
- Windows Sockets [MFC], with archives
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6613e38a19987abcc9f95288e9d1cb6957b076a2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427282"
---
# <a name="windows-sockets-example-of-sockets-using-archives"></a>Windows Sockets: Ejemplo de sockets que usan archivos

Este artículo presenta un ejemplo del uso de la clase [CSocket](../mfc/reference/csocket-class.md). El ejemplo emplea `CArchive` objetos para serializar los datos a través del socket. Tenga en cuenta que esto no es serialización de documentos a o desde un archivo.

El ejemplo siguiente muestra cómo usar el archivo para enviar y recibir datos a través de `CSocket` objetos. El ejemplo está diseñado para que los datos de exchange de dos instancias de la aplicación (en el mismo equipo o en equipos diferentes en la red). Una instancia envía datos, lo que la otra instancia recibe y confirma. Cualquier aplicación puede iniciar un intercambio y actuar como servidor o cliente a la otra aplicación. La siguiente función se define en la clase de vista de la aplicación:

[!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/cpp/windows-sockets-example-of-sockets-using-archives_1.cpp)]

Lo más importante acerca de este ejemplo es que su estructura análoga de MFC `Serialize` función. El `PacketSerialize` función miembro se compone de un **si** instrucción con un **else** cláusula. La función recibe dos [CArchive](../mfc/reference/carchive-class.md) referencias como parámetros: *arData* y *arAck*. Si el *arData* se establece el objeto de almacenamiento para almacenar (enviar), el **si** se ejecuta la bifurcación; de lo contrario, si *arData* está establecido para cargar (recibir), la función toma el **else** rama. Para obtener más información acerca de la serialización en MFC, vea [serialización](../mfc/how-to-make-a-type-safe-collection.md).

> [!NOTE]
>  El *arAck* objeto de almacenamiento se supone que es el opuesto de *arData*. Si *arData* es el envío, *arAck* recibe, y la conversión es verdadera.

Para enviar, la función de ejemplo se repite durante un número especificado de veces, cada vez que genera datos aleatorios para fines de demostración. La aplicación obtendría datos reales desde algún origen, como un archivo. El *arData* operador de inserción del archivo (**<<**) se usa para enviar una secuencia de tres fragmentos consecutivos de datos:

- Un "encabezado" que especifica la naturaleza de los datos (en este caso, el valor de la *bValue* variable y el número de copias que se enviarán).

     Ambos elementos se generan aleatoriamente para este ejemplo.

- El número especificado de copias de los datos.

     Interno **para** bucle envía *bValue* el número de veces especificado.

- Una cadena denominada *strText* que el receptor se muestra a su usuario.

Para la recepción, la función funciona de forma similar, salvo que usa el operador de extracción del archivo (**>>**) para obtener datos desde el archivo. La aplicación receptora comprueba los datos que recibe, muestra el mensaje final de "Recibido" y, a continuación, envía un mensaje que dice "Enviado" para que la aplicación de envío mostrar.

En este modelo de comunicaciones, la palabra "Recibido", se envía el mensaje en el *strText* variable es para su presentación en el otro extremo de la comunicación, por lo que especifica al usuario que ha sido un cierto número de paquetes de datos ha recibido. El receptor responde con una cadena similar que dice "Enviado", para su presentación en pantalla del remitente original. Recepción de ambas cadenas indica que se ha producido una comunicación correcta.

> [!CAUTION]
>  Si está escribiendo un programa de cliente MFC para comunicarse con servidores establecidos (no basados en MFC), no enviar los objetos de C++ a través del archivo. A menos que el servidor es una aplicación MFC que reconozca los tipos de objetos que desea enviar, no podrá recibir y deserializar los objetos. Un ejemplo en el artículo [Windows Sockets: orden de bytes](../mfc/windows-sockets-byte-ordering.md) muestra una comunicación de este tipo.

Para obtener más información, consulte Especificación de Windows Sockets: **htonl**, **htons**, **ntohl**, **ntohs**. Además, para obtener más información, consulte:

- [Windows Sockets: Derivar de las clases de Socket](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets: Cómo funcionan los Sockets con archivos](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets: Nociones](../mfc/windows-sockets-background.md)

## <a name="see-also"></a>Vea también

[Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CArchive::IsStoring](../mfc/reference/carchive-class.md#isstoring)<br/>
[CArchive::operator <<](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive::operator >>](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive::Flush](../mfc/reference/carchive-class.md#flush)<br/>
[CObject:: Serialize](../mfc/reference/cobject-class.md#serialize)

