---
title: 'Windows Sockets: Orden de bytes | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- byte order issues in sockets programming
- sockets [MFC], byte order issues
- Windows Sockets [MFC], byte order issues
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18fc3f586c7fc8861bfc29dade7b62e741bb0ffc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="windows-sockets-byte-ordering"></a>Windows Sockets: Orden de bytes
En este artículo y dos artículos complementarios explican varios aspectos de la programación de Windows Sockets. Este artículo trata el orden de bytes. Los otros temas se tratan en los artículos: [Windows Sockets: bloqueo](../mfc/windows-sockets-blocking.md) y [Windows Sockets: convertir cadenas](../mfc/windows-sockets-converting-strings.md).  
  
 Si usa o derivan de la clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md), deberá administrar estos problemas usted mismo. Si usa o derivan de la clase [CSocket](../mfc/reference/csocket-class.md), MFC los administra automáticamente.  
  
## <a name="byte-ordering"></a>El orden de bytes  
 A veces, distintas arquitecturas de hardware almacenan datos mediante órdenes de bytes diferentes. Por ejemplo, los equipos basados en Intel almacenan datos en el orden inverso de los equipos Macintosh (Motorola). El orden de bytes de Intel, denominado "little-Endian", también es el inverso del orden estándar de red de "big Endian". En la tabla siguiente se describen estos términos.  
  
### <a name="big--and-little-endian-byte-ordering"></a>El orden de bytes big - y Little-Endian  
  
|El orden de bytes|Significado|  
|-------------------|-------------|  
|Big-Endian|El byte más significativo se encuentra en el extremo izquierdo de una palabra.|  
|Little-Endian|El byte más significativo se encuentra en el extremo derecho de una palabra.|  
  
 Normalmente, no tiene que preocuparse acerca de la conversión de orden de bytes de datos que envían y reciben a través de la red, pero hay situaciones en que debe convertir las ordenaciones de bytes.  
  
## <a name="when-you-must-convert-byte-orders"></a>Cuándo debe convertir las ordenaciones de bytes  
 Debe convertir las ordenaciones de bytes en las situaciones siguientes:  
  
-   Pasar información que necesita para interpretar por parte de la red, en lugar de los datos que se envía a otro equipo. Por ejemplo, podría pasar puertos y direcciones, que debe comprender la red.  
  
-   La aplicación de servidor con el que se está comunicando no es una aplicación MFC (y no tiene código fuente para ella). Esto se llama para las conversiones de orden de bytes si los dos equipos no comparten el mismo orden de bytes.  
  
## <a name="when-you-do-not-have-to-convert-byte-orders"></a>Cuando es necesario convertir las ordenaciones de bytes  
 Puede evitar el trabajo de conversión de ordenación de bytes en las situaciones siguientes:  
  
-   Las máquinas en ambos extremos pueden aceptar no intercambiar bytes y ambos equipos utilizan el mismo orden de bytes.  
  
-   El servidor que se está comunicando con es una aplicación MFC.  
  
-   Tiene código fuente para el servidor que se está comunicando, por lo que puede saber explícitamente si debe convertir las ordenaciones de bytes o no.  
  
-   Puede trasladar el servidor a MFC. Esto es bastante fácil de hacer y el resultado suele ser código más pequeño, más rápido.  
  
 Trabajar con [CAsyncSocket](../mfc/reference/casyncsocket-class.md), debe administrar las conversiones necesarias de orden de bytes. Windows Sockets normaliza el modelo de orden de bytes "big Endian" y proporciona funciones para convertir entre esta ordenación y otras personas. [CArchive](../mfc/reference/carchive-class.md), sin embargo, que se usa con [CSocket](../mfc/reference/csocket-class.md), usa la inversa ("little-Endian"), pero `CArchive` se ocupa de los detalles de las conversiones de orden de bytes. Mediante esta ordenación estándar en sus aplicaciones, o mediante funciones de conversión de Windows Sockets: orden de bytes, puede que el código más portable.  
  
 El caso ideal para utilizar sockets de MFC es cuando se escribe en ambos extremos de la comunicación y se usa MFC en ambos extremos. Si está escribiendo una aplicación que se comunicará con aplicaciones no están basados en MFC, como un servidor FTP, probablemente necesitará administrar el intercambio de bytes antes de pasar los datos en el objeto de archivo, utilizando las rutinas de conversión de Windows Sockets **ntohs**, **ntohl**, **htons**, y **htonl**. Un ejemplo de estas funciones utilizadas en las comunicaciones con una aplicación MFC no aparece más adelante en este artículo.  
  
> [!NOTE]
>  Cuando el otro extremo de la comunicación no es una aplicación MFC, también deberá evitar la transmisión por secuencias de objetos de C++ derivados de `CObject` en el archivo porque el destinatario no podrá controlarlos. Vea la nota de [Windows Sockets: usar Sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md).  
  
 Para obtener más información acerca de los pedidos de bytes, vea la especificación de Windows Sockets, disponible en el SDK de Windows.  
  
## <a name="a-byte-order-conversion-example"></a>Un ejemplo de conversión de orden de bytes  
 En el ejemplo siguiente se muestra una función de serialización para un `CSocket` objeto que usa un archivo. También ilustra el uso de las funciones de conversión de orden de bytes en la API de Windows Sockets.  
  
 En este ejemplo se muestra un escenario en el que está escribiendo a un cliente que se comunica con una aplicación de servidor no están basados en MFC para el que se no tienen acceso al código fuente. En este escenario, debe asumir que el servidor no están basados en MFC utiliza el orden de bytes de red estándar. En cambio, la aplicación de cliente MFC utiliza una `CArchive` objeto con un `CSocket` objeto, y `CArchive` utiliza el orden de bytes "little-Endian", el efecto contrario de la red estándar.  
  
 Suponga que el servidor no están basados en MFC con la que tiene previsto comunicarse tiene un protocolo establecido para un paquete de mensaje similar al siguiente:  
  
 [!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_1.cpp)]  
  
 En términos MFC, esto se expresaría como sigue:  
  
 [!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_2.cpp)]  
  
 En C++, un `struct` es básicamente lo mismo que una clase. El `Message` estructura puede tener funciones miembro, como la `Serialize` función miembro declarada anteriormente. El `Serialize` función miembro podría ser similar al siguiente:  
  
 [!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_3.cpp)]  
  
 En este ejemplo se llama para las conversiones de orden de bytes de datos porque hay una correspondencia clara entre el orden de bytes de la aplicación del servidor no están basados en MFC en uno de los extremos y el `CArchive` utilizado en la aplicación de cliente MFC en el otro extremo. El ejemplo ilustra algunas de las funciones de conversión de orden de bytes que proporciona Windows Sockets. En la tabla siguiente describe estas funciones.  
  
### <a name="windows-sockets-byte-order-conversion-functions"></a>Funciones de conversión de orden de bytes de Windows Sockets  
  
|Función|Propósito|  
|--------------|-------------|  
|**ntohs**|Convierte una cantidad de 16 bits de orden de bytes de la red al orden de bytes del host (de big-Endian a little-Endian).|  
|**ntohl**|Convierte una cantidad de 32 bits de orden de bytes de la red al orden de bytes del host (de big-Endian a little-Endian).|  
|**Htons**|Convierte una cantidad de 16 bits de orden de bytes del host al orden de bytes de red (de little-Endian a big-Endian).|  
|**Htonl**|Convierte una cantidad de 32 bits de orden de bytes del host al orden de bytes de red (de little-Endian a big-Endian).|  
  
 Otro punto de este ejemplo es que cuando la aplicación de socket en el otro extremo de la comunicación es una aplicación no basada en MFC, debe evitar hacer algo similar al siguiente:  
  
 `ar << pMsg;`  
  
 donde `pMsg` es un puntero a un objeto de C++ que se deriva de la clase `CObject`. Esto enviará información de MFC adicional asociada a objetos y el servidor no comprenderá, tal y como lo haría si se tratara de una aplicación MFC.  
  
 Para obtener más información, consulte:  
  
-   [Windows Sockets: Usar la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets: Nociones](../mfc/windows-sockets-background.md)  
  
-   [Windows Sockets: Sockets de flujos](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets: Sockets de datagramas](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>Vea también  
 [Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)

