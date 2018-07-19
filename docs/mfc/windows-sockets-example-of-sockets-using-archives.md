---
title: 'Windows Sockets: Ejemplo de Sockets que usan archivos | Documentos de Microsoft'
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
ms.openlocfilehash: 942c3e8aa2aeccefc9c92cd9fd32d453dc5353cf
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956432"
---
# <a name="windows-sockets-example-of-sockets-using-archives"></a>Windows Sockets: Ejemplo de sockets que usan archivos
En este artículo se presenta un ejemplo del uso de la clase [CSocket](../mfc/reference/csocket-class.md). En el ejemplo se emplea `CArchive` objetos para serializar datos a través de un socket. Tenga en cuenta que esto no es serialización de documentos a o desde un archivo.  
  
 En el ejemplo siguiente se muestra cómo usar el archivo para enviar y recibir datos a través de `CSocket` objetos. El ejemplo está diseñado para que los datos de exchange de dos instancias de la aplicación (en el mismo equipo o en equipos diferentes en la red). Una instancia envía datos, lo que la otra instancia recibe y lo confirma. Cualquier aplicación puede iniciar un intercambio y cualquiera puede actuar como servidor o cliente a la otra aplicación. La siguiente función se define en la clase de vista de la aplicación:  
  
 [!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/cpp/windows-sockets-example-of-sockets-using-archives_1.cpp)]  
  
 Lo más importante acerca de este ejemplo es que asemeja a su estructura de MFC `Serialize` función. El `PacketSerialize` función miembro se compone de un **si** instrucción con un **else** cláusula. La función recibe dos [CArchive](../mfc/reference/carchive-class.md) referencias como parámetros: *arData* y *arAck*. Si el *arData* objeto de almacenamiento está configurado para almacenar (enviar), el **si** se ejecuta la bifurcación; en caso contrario, si *arData* se establece para cargar (recibir), la función toma el **else** bifurcación. Para obtener más información acerca de la serialización en MFC, vea [serialización](../mfc/how-to-make-a-type-safe-collection.md).  
  
> [!NOTE]
>  El *arAck* objeto de almacenamiento se supone que es el opuesto de *arData*. Si *arData* es para el envío, *arAck* recibe, y la conversión es verdadera.  
  
 Para enviar, la función de ejemplo se crea un bucle durante un número especificado de veces, cada vez que genera algunos datos aleatorios para fines de demostración. La aplicación obtendría datos reales desde algún origen, como un archivo. El *arData* operador de inserción del archivo (**<<**) se usa para enviar una secuencia de tres segmentos consecutivos de datos:  
  
-   Un "encabezado" que especifica la naturaleza de los datos (en este caso, el valor de la *bValue* variable y el número de copias que se enviarán).  
  
     Ambos elementos se generan aleatoriamente para este ejemplo.  
  
-   El número especificado de copias de los datos.  
  
     Interna **para** bucle envía *bValue* el número de veces especificado.  
  
-   Llama a una cadena *strText* que el receptor muestra al usuario.  
  
 Para recibir, la función funciona de forma similar, salvo que usa el operador de extracción del archivo (**>>**) para obtener datos desde el archivo. La aplicación receptora comprueba los datos que recibe, muestra el mensaje de "Recibido" final y, a continuación, envía un mensaje que dice "Enviado" en la aplicación de envío mostrar.  
  
 En este modelo de comunicaciones, la palabra "Recibido", se envía el mensaje en el *strText* variable, es para su presentación en el otro extremo de la comunicación, por lo que especifica para el usuario que recibe que ha sido un número determinado de paquetes de datos se recibió. El receptor responde con una cadena similar que dice "Enviado", para su presentación en pantalla del remitente original. Recepción de ambas cadenas indica que se ha producido una comunicación correcta.  
  
> [!CAUTION]
>  Si está escribiendo un programa de cliente MFC para comunicarse con servidores establecidos (no basados en MFC), no enviar objetos de C++ a través del archivo. A menos que el servidor es una aplicación MFC que entienda los tipos de objetos que desea enviar, no podrá recibir ni deserializar los objetos. Un ejemplo en el artículo [Windows Sockets: orden de bytes](../mfc/windows-sockets-byte-ordering.md) muestra una comunicación de este tipo.  
  
 Para obtener más información, vea la especificación de Windows Sockets: **htonl**, **htons**, **ntohl**, **ntohs**. Además, para obtener más información, vea:  
  
-   [Windows Sockets: Derivar de las clases de Socket](../mfc/windows-sockets-deriving-from-socket-classes.md)  
  
-   [Windows Sockets: Cómo funcionan los Sockets con archivos](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows Sockets: Nociones](../mfc/windows-sockets-background.md)  
  
## <a name="see-also"></a>Vea también  
 [Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)   
 [CArchive::IsStoring](../mfc/reference/carchive-class.md#isstoring)   
 [CArchive::operator <<](../mfc/reference/carchive-class.md#operator_lt_lt)   
 [CArchive::operator >>](../mfc/reference/carchive-class.md#operator_lt_lt)   
 [CArchive::Flush](../mfc/reference/carchive-class.md#flush)   
 [CObject:: Serialize](../mfc/reference/cobject-class.md#serialize)

