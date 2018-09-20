---
title: 'Windows Sockets: Orden de bytes | Microsoft Docs'
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
ms.openlocfilehash: feaf2c02dbb17272696571ba27a077e6e99836b0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377199"
---
# <a name="windows-sockets-byte-ordering"></a>Windows Sockets: Orden de bytes

En este artículo y dos artículos complementarios explican varios problemas en la programación de Windows Sockets. Este artículo describe el orden de bytes. Los otros temas se tratan en los artículos: [Windows Sockets: bloquear](../mfc/windows-sockets-blocking.md) y [Windows Sockets: convertir cadenas](../mfc/windows-sockets-converting-strings.md).

Si usa o derivar de la clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md), tendrá que administrar estos problemas por su cuenta. Si usa o derivar de la clase [CSocket](../mfc/reference/csocket-class.md), MFC administra automáticamente.

## <a name="byte-ordering"></a>Orden de bytes

Las arquitecturas de diferentes máquinas a veces, almacenan de datos mediante órdenes de bytes diferentes. Por ejemplo, las máquinas de basados en Intel almacenan datos en orden inverso de las máquinas de Macintosh (Motorola). El orden de bytes de Intel, denominado "little-Endian," también es el inverso del orden estándar de red de "big Endian". La siguiente tabla explica estos términos.

### <a name="big--and-little-endian-byte-ordering"></a>Orden de bytes big y Little-Endian

|Orden de bytes|Significado|
|-------------------|-------------|
|Big-Endian|Es el byte más significativo en el extremo izquierdo de una palabra.|
|Little-Endian|Es el byte más significativo en el extremo derecho de una palabra.|

Normalmente, no tiene que preocuparse acerca de la conversión de orden de bytes de datos que envían y reciben a través de la red, pero hay situaciones en que debe convertir las ordenaciones de bytes.

## <a name="when-you-must-convert-byte-orders"></a>Cuándo debe convertir las órdenes de bytes

Deberá convertir las ordenaciones de bytes en las situaciones siguientes:

- Se pasa la información que necesita para interpretar la red, a diferencia de los datos que se va a enviar a otra máquina. Por ejemplo, podría pasar los puertos y direcciones, que debe entender la red.

- La aplicación de servidor con el que se está comunicando no es una aplicación MFC (y no tiene código fuente para él). Esto se llama para las conversiones de orden de bytes si las dos máquinas no comparten el mismo orden de bytes.

## <a name="when-you-do-not-have-to-convert-byte-orders"></a>Cuando no tiene que convertir el orden de bytes little

Puede evitar el trabajo de conversión de ordenación de bytes en las situaciones siguientes:

- Las máquinas en ambos extremos pueden aceptar la no intercambiar bytes y ambos equipos utilizan el mismo orden de bytes.

- El servidor con que se comunican es una aplicación MFC.

- Tiene código fuente para el servidor que se está comunicando con, por lo que puede indicar explícitamente si debe convertir las órdenes de bytes o no.

- Puede trasladar el servidor a MFC. Esto es bastante fácil de hacer, y el resultado suele ser código más rápido y más pequeños.

Trabajar con [CAsyncSocket](../mfc/reference/casyncsocket-class.md), debe administrar las conversiones necesarias de orden de bytes. Windows Sockets normaliza el modelo de orden de bytes "big Endian" y proporciona funciones para convertir entre este orden y otros. [CArchive](../mfc/reference/carchive-class.md), sin embargo, que se usa con [CSocket](../mfc/reference/csocket-class.md), utiliza el orden contrario ("little-Endian"), pero `CArchive` se encarga de los detalles de las conversiones de orden de bytes. Mediante esta ordenación estándar en sus aplicaciones, o mediante funciones de conversión de Windows Sockets: orden de bytes, puede hacer que su código más portable.

El caso ideal para utilizar sockets de MFC es cuando se escribe en ambos extremos de la comunicación y se usa MFC en ambos extremos. Si está escribiendo una aplicación que se comunican con las aplicaciones no basados en MFC, como un servidor FTP, probablemente necesitará administrar el intercambio de bytes antes de pasar datos al objeto de archivo, utilizando las rutinas de conversión de Windows Sockets **ntohs**, **ntohl**, **htons**, y **htonl**. Un ejemplo de estas funciones que se usa para establecer comunicación con una aplicación MFC no aparece más adelante en este artículo.

> [!NOTE]
>  Cuando el otro extremo de la comunicación no es una aplicación MFC, también se debe evitar los objetos de C++ que se deriva de transmisión por secuencias `CObject` en el archivo porque el receptor no podrá controlarlos. Vea la nota de [Windows Sockets: usar Sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md).

Para obtener más información acerca de los pedidos de bytes, vea la especificación de Windows Sockets, disponible en el SDK de Windows.

## <a name="a-byte-order-conversion-example"></a>Un ejemplo de conversión de orden de bytes

El ejemplo siguiente muestra una función de serialización para un `CSocket` objeto que usa un archivo. También muestra el uso de las funciones de conversión de orden de bytes de la API de Windows Sockets.

En este ejemplo se presenta un escenario en el que está escribiendo a un cliente que se comunica con una aplicación de servidor no basados en MFC para que no tiene acceso al código fuente. En este escenario, se debe suponer que el servidor de no MFC utiliza el orden de bytes de red estándar. En cambio, la aplicación de cliente MFC usa una `CArchive` objeto con un `CSocket` objeto, y `CArchive` utiliza el orden de bytes "little-Endian", lo opuesto de la red estándar.

Supongamos que el servidor no basados en MFC con la que va a comunicar tiene un protocolo establecido para el paquete de un mensaje similar al siguiente:

[!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_1.cpp)]

En términos MFC, esto se expresaría como sigue:

[!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_2.cpp)]

En C++, un **struct** es básicamente lo mismo que una clase. El `Message` estructura puede tener funciones miembro, como la `Serialize` función miembro declarado anteriormente. El `Serialize` función miembro podría tener este aspecto:

[!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_3.cpp)]

Este ejemplo se llama para las conversiones de orden de bytes de datos porque hay una correspondencia clara entre el orden de bytes de la aplicación de servidor no basados en MFC en un extremo y la `CArchive` utilizados en la aplicación de cliente MFC en el otro extremo. El ejemplo ilustra algunas de las funciones de conversión de orden de bytes que proporciona Windows Sockets. En la tabla siguiente se describe estas funciones.

### <a name="windows-sockets-byte-order-conversion-functions"></a>Funciones de conversión de orden de bytes de Windows Sockets

|Función|Propósito|
|--------------|-------------|
|**ntohs**|Convierte una cantidad de 16 bits de orden de bytes de red al orden de bytes del host (de big-Endian a little-Endian).|
|**ntohl**|Convierte una cantidad de 32 bits de orden de bytes de red al orden de bytes del host (de big-Endian a little-Endian).|
|**Htons**|Convierte una cantidad de 16 bits de orden de bytes del host al orden de bytes de red (de little-Endian a big-Endian).|
|**Htonl**|Convierte una cantidad de 32 bits de orden de bytes del host al orden de bytes de red (de little-Endian a big-Endian).|

Otro aspecto de este ejemplo es que cuando la aplicación de socket en el otro extremo de la comunicación es una aplicación no basados en MFC, debe evitar hacer algo parecido a lo siguiente:

`ar << pMsg;`

donde `pMsg` es un puntero a un objeto de C++ derivado de la clase `CObject`. Esto enviará información de MFC adicional asociada a objetos y el servidor no comprenderá, como lo haría si se tratara de una aplicación MFC.

Para obtener más información, consulte:

- [Windows Sockets: Usar la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Nociones](../mfc/windows-sockets-background.md)

- [Windows Sockets: Sockets de flujos](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Sockets de datagramas](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Vea también

[Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)

