---
title: 'Windows Sockets: Usar la clase CAsyncSocket | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CAsyncSocket
dev_langs:
- C++
helpviewer_keywords:
- CAsyncSocket class [MFC], programming model
- Windows Sockets [MFC], asynchronous
- sockets [MFC], converting between Unicode and MBCS strings
- SOCKET handle
- sockets [MFC], asynchronous operation
- Windows Sockets [MFC], converting Unicode and MBCS strings
ms.assetid: 825dae17-7c1b-4b86-8d6c-da7f1afb5d8d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc461a0a2325f768711f6d7529949ee24a1b4a25
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954889"
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows Sockets: Usar la clase CAsyncSocket
Este artículo explica cómo utilizar la clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md). Tenga en cuenta que esta clase encapsula la API de Windows Sockets en un nivel muy bajo. `CAsyncSocket` está destinado a los programadores que conocer en detalle las comunicaciones de red, pero desean la comodidad de devoluciones de llamada para recibir notificaciones de eventos de la red. Según esta suposición, este artículo proporciona sólo la instrucción básica. Probablemente le convendrá usar `CAsyncSocket` si desea accesibilidad ofrece Windows Sockets de trabajar con varios protocolos de red en una aplicación MFC, pero no desea sacrificar la flexibilidad. También podría notar que puede obtener una mayor eficacia al programar las comunicaciones más directamente por sí mismo de las que podría utilizando el modelo alternativo más general de clase `CSocket`.  
  
 `CAsyncSocket` se documenta en la *referencia de MFC*. Visual C++ también proporciona la especificación de Windows Sockets, incluida en el SDK de Windows. Los detalles se dejan a usted. Visual C++ no proporciona una aplicación de ejemplo para `CAsyncSocket`.  
  
 Si no tiene muchos conocimientos acerca de las comunicaciones de red y desea una solución sencilla, utilice la clase [CSocket](../mfc/reference/csocket-class.md) con un `CArchive` objeto. Vea [Windows Sockets: usar Sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md) para obtener más información.  
  
 En este artículo se tratan los aspectos siguientes:  
  
-   Crear y usar un `CAsyncSocket` objeto.  
  
-   [Sus responsabilidades con CAsyncSocket](#_core_your_responsibilities_with_casyncsocket).  
  
##  <a name="_core_creating_and_using_a_casyncsocket_object"></a> Crear y utilizar un objeto CAsyncSocket  
  
#### <a name="to-use-casyncsocket"></a>Para utilizar CAsyncSocket  
  
1.  Construir un [CAsyncSocket](../mfc/reference/casyncsocket-class.md) de objetos y utilizar el objeto para crear subyacente **SOCKET** controlar.  
  
     Creación de un socket sigue el patrón MFC de construcción en dos fases.  
  
     Por ejemplo:  
  
     [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]  
  
     O bien  
  
     [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]  
  
     El primer constructor anterior crea un `CAsyncSocket` objeto en la pila. El segundo constructor crea un `CAsyncSocket` en el montón. La primera [crear](../mfc/reference/casyncsocket-class.md#create) llamada anterior utiliza los parámetros predeterminados para crear un socket de secuencia. El segundo `Create` llamada crea un socket de datagrama con una dirección y el puerto especificado. (Puede usar `Create` versión con cualquier método de construcción.)  
  
     Los parámetros de `Create` son:  
  
    -   Un "puerto": un entero corto.  
  
         Para un socket de servidor, debe especificar un puerto. Para un socket de cliente, normalmente se acepte el valor predeterminado para este parámetro, que permite a Windows Sockets seleccionar un puerto.  
  
    -   Un tipo de socket: **SOCK_STREAM** (valor predeterminado) o **SOCK_DGRAM**.  
  
    -   Un socket "dirección", como "ftp.microsoft.com" o "128.56.22.8".  
  
         Se trata de la dirección de protocolo de Internet (IP) en la red. Probablemente siempre se basará en el valor predeterminado para este parámetro.  
  
     Se explica los términos "puerto" y "dirección de socket" en [Windows Sockets: puertos y direcciones de Socket](../mfc/windows-sockets-ports-and-socket-addresses.md).  
  
2.  Si el socket es un cliente, conecte el objeto socket a un servidor de socket, con [CAsyncSocket:: Connect](../mfc/reference/casyncsocket-class.md#connect).  
  
     O bien  
  
     Si el socket es un servidor, configure el socket para empezar a escuchar (con [CAsyncSocket:: Listen](../mfc/reference/casyncsocket-class.md#listen)) para los intentos de conexión desde un cliente. Al recibir una solicitud de conexión, acepte con [CAsyncSocket:: Accept](../mfc/reference/casyncsocket-class.md#accept).  
  
     Después de aceptar una conexión, puede realizar tareas como la validación de contraseñas.  
  
    > [!NOTE]
    >  El `Accept` función miembro toma una referencia a una nueva y vacía `CSocket` objeto como su parámetro. Se debe crear este objeto antes de llamar a `Accept`. Si este objeto socket se sale del ámbito, se cierra la conexión. No llame a `Create` para este nuevo objeto de socket. Para obtener un ejemplo, vea el artículo [Windows Sockets: secuencia de operaciones](../mfc/windows-sockets-sequence-of-operations.md).  
  
3.  Para realizar comunicaciones con otros sockets mediante una llamada a la `CAsyncSocket` funciones de miembro del objeto que encapsulan las funciones de API de Windows Sockets.  
  
     Vea la especificación de Windows Sockets y la clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md) en el *referencia de MFC*.  
  
4.  Destruir el `CAsyncSocket` objeto.  
  
     Si ha creado el objeto de socket en la pila, su destructor se llama cuando la función contenedora se sale del ámbito. Si ha creado el objeto de socket en el montón, usando la **nueva** (operador), tú eres responsable de uso de la **eliminar** operador que se va a destruir el objeto.  
  
     El destructor llama al método del objeto [cerrar](../mfc/reference/casyncsocket-class.md#close) función miembro antes de destruir el objeto.  
  
 Para obtener un ejemplo de esta secuencia en el código (en realidad, para un `CSocket` objeto), consulte [Windows Sockets: secuencia de operaciones](../mfc/windows-sockets-sequence-of-operations.md).  
  
##  <a name="_core_your_responsibilities_with_casyncsocket"></a> Sus responsabilidades con CAsyncSocket  
 Cuando se crea un objeto de clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md), encapsula el objeto de una ventana de **SOCKET** controlar y proporciona operaciones en ese identificador. Cuando usas `CAsyncSocket`, debe tratar con todos los problemas que puede enfrentarse si se utiliza la API directamente. Por ejemplo:  
  
-   Escenarios de "Bloqueo".  
  
-   Diferencias entre el envío y recepción de máquinas del orden de bytes.  
  
-   Convertir entre Unicode y juegos de caracteres multibyte conjunto de cadenas (MBCS).  
  
 Para obtener definiciones de estos términos e información adicional, consulte [Windows Sockets: bloqueo](../mfc/windows-sockets-blocking.md), [Windows Sockets: orden de bytes](../mfc/windows-sockets-byte-ordering.md), [Windows Sockets: convertir cadenas](../mfc/windows-sockets-converting-strings.md) .  
  
 A pesar de estos problemas, clase `CAsycnSocket` puede ser la opción más adecuada para usted si la aplicación requiere toda la flexibilidad y control puede obtener. Si no es así, debe considerar el uso de la clase `CSocket` en su lugar. `CSocket` oculta una gran cantidad de detalle del usuario: TI surtidores de mensajes durante llamadas de bloqueo de Windows y proporciona acceso a `CArchive`, que administra las diferencias de orden de bytes y la conversión de cadenas.  
  
 Para obtener más información, consulte:  
  
-   [Windows Sockets: Nociones](../mfc/windows-sockets-background.md)  
  
-   [Windows Sockets: Sockets de flujos](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets: Sockets de datagramas](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>Vea también  
 [Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)

