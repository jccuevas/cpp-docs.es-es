---
title: "Windows Sockets: Usar la clase CAsyncSocket | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CAsyncSocket"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAsyncSocket (clase), modelo de programación"
  - "SOCKET (controlador)"
  - "sockets [C++], operación asincrónica"
  - "sockets [C++], convertir entre cadenas Unicode y MBCS"
  - "Windows Sockets [C++], asincrónico"
  - "Windows Sockets [C++], convertir cadenas Unicode y MBCS"
ms.assetid: 825dae17-7c1b-4b86-8d6c-da7f1afb5d8d
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Sockets: Usar la clase CAsyncSocket
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica cómo utilizar la clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md).  Tenga en cuenta que esta clase encapsula el Windows Sockets API en un muy bajo.  `CAsyncSocket` es para uso de los programadores que conocen comunicaciones por red detalladamente pero desea comodidad de las devoluciones de llamada para la notificación de los eventos de la red.  Según esta suposición, este artículo sólo proporciona la instrucción básica.  Debería considerar probablemente utilizar `CAsyncSocket` si desea que la facilidad de Windows Sockets de tratar de protocolos de red en una aplicación MFC pero no desea sacrificar flexibilidad.  Puede que también de que puede obtener una mejor eficacia programando las comunicaciones más directamente personalmente que podría con el modelo alternativo más general de la clase `CSocket`.  
  
 `CAsyncSocket` se documenta en la *referencia de MFC*.  De Visual C\+\+ también proporciona la especificación de Windows Sockets, establecida en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  Los detalles se dejan se.  Visual C\+\+ no proporciona una aplicación de ejemplo para `CAsyncSocket`.  
  
 Si no está muy bien informa sobre comunicaciones por red y no desea una solución sencilla, utilice la clase [CSocket](../mfc/reference/csocket-class.md) con un objeto de `CArchive` .  Vea [Windows Sockets: Mediante sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md) para obtener más información.  
  
 Este artículo trata:  
  
-   Crear y con un objeto de `CAsyncSocket` .  
  
-   [Las responsabilidades con CAsyncSocket](#_core_your_responsibilities_with_casyncsocket).  
  
##  <a name="_core_creating_and_using_a_casyncsocket_object"></a> El crear y Utilizar un objeto de CAsyncSocket  
  
#### Para utilizar CAsyncSocket  
  
1.  Crea un objeto de [CAsyncSocket](../mfc/reference/casyncsocket-class.md) y utilizar el objeto para crear el identificador subyacente de **SOCKET** .  
  
     La creación de un socket sigue el modelo de MFC de construcción de dos pasos.  
  
     Por ejemplo:  
  
     [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/CPP/windows-sockets-using-class-casyncsocket_1.cpp)]  
  
     O bien  
  
     [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/CPP/windows-sockets-using-class-casyncsocket_2.cpp)]  
  
     El primer constructor anterior crea un objeto de `CAsyncSocket` en la pila.  El segundo constructor crea `CAsyncSocket` en la pila.  La primera llamada de [crear](../Topic/CAsyncSocket::Create.md) anterior utiliza parámetros predeterminados para crear un socket de secuencia.  La segunda llamada de **crear** crea un socket de datagrama con un puerto y una dirección especificados. \(Puede usar cualquier versión de **crear** con cualquier método de construcción.\)  
  
     Los parámetros a **crear** son:  
  
    -   Un “puerto”: un entero corto.  
  
         Para un socket de servidor, debe especificar un puerto.  Para un socket de cliente, se acepta normalmente el valor predeterminado de este parámetro, que permite el Windows Sockets seleccionar un puerto.  
  
    -   Un socket tipo: **SOCK\_STREAM** \(valor predeterminado\) o **SOCK\_DGRAM**.  
  
    -   Un socket “dirección”, por ejemplo “ftp.microsoft.com” o “128.56.22.8”.  
  
         Ésta es la dirección de \(IP\) de protocolo de Internet en la red.  Se confía probablemente siempre en el valor predeterminado para este parámetro.  
  
     Los términos “puerto” y “dirección de socket” se explican en [Windows Sockets: Puertos y direcciones de socket](../mfc/windows-sockets-ports-and-socket-addresses.md).  
  
2.  Si el socket es un cliente, conectar el objeto de socket a un socket de servidor, mediante [CAsyncSocket::Connect](../Topic/CAsyncSocket::Connect.md).  
  
     O bien  
  
     Si el socket es un servidor, establezca el socket para iniciar escuchando \(con [CAsyncSocket::Listen](../Topic/CAsyncSocket::Listen.md)\) para los intentos se conectan de un cliente.  Al recibir una solicitud de conexión, aceptela con [CAsyncSocket::Accept](../Topic/CAsyncSocket::Accept.md).  
  
     Después de aceptar una conexión, puede realizar tareas como validando contraseñas.  
  
    > [!NOTE]
    >  La función miembro de **Aceptar** toma una referencia a un nuevo, vacío objeto de `CSocket` como parámetro.  Debe construir este objeto antes de llamar a **Aceptar**.  Si este objeto de socket sale del ámbito, la conexión se cierra.  No llame a **crear** para este nuevo objeto de socket.  Para obtener un ejemplo, vea el artículo [Windows Sockets: Secuencia de operaciones](../mfc/windows-sockets-sequence-of-operations.md).  
  
3.  Realice las comunicaciones con otros sockets a las funciones miembro del objeto de `CAsyncSocket` que encapsulan funciones de la API de Windows Sockets.  
  
     Vea el Windows Sockets especificación y la clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md) en *la referencia de MFC*.  
  
4.  Destruya el objeto de `CAsyncSocket` .  
  
     Si creó el objeto de socket en la pila, se llama al destructor cuando la función que contiene sale del ámbito.  Si creó el objeto de socket en la pila, mediante el operador de **new** , es responsable de utilizar el operador de **borrar** para destruir el objeto.  
  
     Destructor llama a la función miembro de [cerrar](../Topic/CAsyncSocket::Close.md) de objeto antes de destruir el objeto.  
  
 Para obtener un ejemplo de esta secuencia en código \(realmente para un objeto de `CSocket` \), vea [Windows Sockets: Secuencia de operaciones](../mfc/windows-sockets-sequence-of-operations.md).  
  
##  <a name="_core_your_responsibilities_with_casyncsocket"></a> El Responsibilities con CAsyncSocket  
 Cuando se crea un objeto de clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md), el objeto encapsula un identificador de Windows **SOCKET** y operaciones de fuentes en ese identificador.  Cuando se utiliza `CAsyncSocket`, debe tratar con todos los problemas que puede hacer nuevo si usó API directamente.  Por ejemplo:  
  
-   “Bloqueo” escenarios.  
  
-   Diferencias de orden de bytes entre equipos de enviar y recibir.  
  
-   El convertir Unicode y cadenas de juego de caracteres multibyte \(MBCS\).  
  
 Para obtener definiciones de estos términos e información adicional, vea [Windows Sockets: Bloquear](../mfc/windows-sockets-blocking.md), [Windows Sockets: El orden de byte](../mfc/windows-sockets-byte-ordering.md), [Windows Sockets: Convertir cadenas](../mfc/windows-sockets-converting-strings.md).  
  
 A pesar de estos problemas, la clase **CAsycnSocket** puede ser la opción correcta automáticamente si la aplicación requiere toda la flexibilidad y los controles puede obtener.  Si no, considere el uso de la clase `CSocket` en su lugar.  `CSocket` oculta mucho detalle de permite: bombea los mensajes de Windows durante las llamadas de bloqueo y proporciona acceso a `CArchive`, que administra diferencias de orden de bytes y la conversión de cadenas para usted.  
  
 Para obtener más información, vea:  
  
-   [Windows Sockets: En segundo plano](../mfc/windows-sockets-background.md)  
  
-   [Windows Sockets: Sockets de secuencia](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets: Sockets de datagrama](../mfc/windows-sockets-datagram-sockets.md)  
  
## Vea también  
 [Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)