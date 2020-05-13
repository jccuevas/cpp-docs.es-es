---
title: 'Windows Sockets: Orden de bytes'
ms.date: 11/04/2016
helpviewer_keywords:
- byte order issues in sockets programming
- sockets [MFC], byte order issues
- Windows Sockets [MFC], byte order issues
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
ms.openlocfilehash: 50548202483c4d9d4471ad2c600270c4df4503e7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371057"
---
# <a name="windows-sockets-byte-ordering"></a>Windows Sockets: Orden de bytes

Este artículo y dos artículos complementarios explican varios problemas en la programación de Windows Sockets. En este artículo se trata el orden de bytes. Los otros problemas se tratan en los artículos: [Windows Sockets: Blocking](../mfc/windows-sockets-blocking.md) y [Windows Sockets: Converting Strings](../mfc/windows-sockets-converting-strings.md).

Si usa o deriva de la clase [CAsyncSocket](../mfc/reference/casyncsocket-class.md), deberá administrar estos problemas usted mismo. Si utiliza o deriva de la clase [CSocket](../mfc/reference/csocket-class.md), MFC los administra por usted.

## <a name="byte-ordering"></a>ordenación de bytes

Diferentes arquitecturas de máquina a veces almacenan datos utilizando diferentes órdenes de bytes. Por ejemplo, las máquinas basadas en Intel almacenan datos en el orden inverso de las máquinas Macintosh (Motorola). El orden de bytes de Intel, llamado "little-Endian", es también el reverso del orden "big-Endian" estándar de red. En la tabla siguiente se explican estos términos.

### <a name="big--and-little-endian-byte-ordering"></a>Orden de bytes grandes y pequeños endian

|Ordenación de bytes|Significado|
|-------------------|-------------|
|Big-Endian|El byte más significativo está en el extremo izquierdo de una palabra.|
|Little-Endian|El byte más significativo está en el extremo derecho de una palabra.|

Normalmente, no tiene que preocuparse por la conversión de orden de bytes para los datos que envía y recibe a través de la red, pero hay situaciones en las que debe convertir pedidos de bytes.

## <a name="when-you-must-convert-byte-orders"></a>When You Must Convert Byte Orders

Debe convertir órdenes de bytes en las siguientes situaciones:

- Está pasando información que necesita ser interpretada por la red, a diferencia de los datos que está enviando a otra máquina. Por ejemplo, puede pasar puertos y direcciones, que la red debe comprender.

- La aplicación de servidor con la que se está comunicando no es una aplicación MFC (y no tiene código fuente para ella). Esto requiere conversiones de orden de bytes si las dos máquinas no comparten el mismo orden de bytes.

## <a name="when-you-do-not-have-to-convert-byte-orders"></a>Cuando no tiene que convertir órdenes de bytes

Puede evitar el trabajo de convertir órdenes de bytes en las siguientes situaciones:

- Las máquinas en ambos extremos pueden acordar no intercambiar bytes y ambas máquinas usan el mismo orden de bytes.

- El servidor con el que se está comunicando es una aplicación MFC.

- Tiene código fuente para el servidor con el que se está comunicando, por lo que puede saber explícitamente si debe convertir órdenes de bytes o no.

- Puede migrar el servidor a MFC. Esto es bastante fácil de hacer, y el resultado suele ser un código más pequeño y más rápido.

Al trabajar con [CAsyncSocket](../mfc/reference/casyncsocket-class.md), debe administrar las conversiones de orden de bytes necesarias usted mismo. Windows Sockets estandariza el modelo de orden de bytes "big-Endian" y proporciona funciones para convertir entre este orden y otros. [CArchive](../mfc/reference/carchive-class.md), sin embargo, que se utiliza con [CSocket](../mfc/reference/csocket-class.md), `CArchive` utiliza el orden opuesto ("little-Endian"), pero se encarga de los detalles de las conversiones de orden de bytes para usted. Mediante este orden estándar en las aplicaciones o mediante las funciones de conversión de orden de bytes de Windows Sockets, puede hacer que el código sea más portátil.

El caso ideal para utilizar sockets de MFC es cuando se escribe en ambos extremos de la comunicación y se usa MFC en ambos extremos. Si está escribiendo una aplicación que se comunicará con aplicaciones que no son MFC, como un servidor FTP, probablemente tendrá que administrar el intercambio de bytes antes de pasar datos al objeto de archivado, utilizando las rutinas de conversión de Windows Sockets **ntohs**, **ntohl**, **htons**y **htonl**. Un ejemplo de estas funciones utilizadas en la comunicación con una aplicación que no es MFC aparece más adelante en este artículo.

> [!NOTE]
> Cuando el otro extremo de la comunicación no es una aplicación MFC, `CObject` también debe evitar la transmisión por secuencias de objetos C++ derivados del archivo porque el receptor no podrá controlarlos. Consulte la nota en [Windows Sockets: Uso](../mfc/windows-sockets-using-sockets-with-archives.md)de sockets con archivos .

Para obtener más información acerca de los pedidos de bytes, vea la especificación de Windows Sockets, disponible en el Windows SDK.

## <a name="a-byte-order-conversion-example"></a>Un ejemplo de conversión de orden de bytes

En el ejemplo siguiente se `CSocket` muestra una función de serialización para un objeto que utiliza un archivo. También ilustra el uso de las funciones de conversión de orden de bytes en la API de Windows Sockets.

En este ejemplo se presenta un escenario en el que se escribe un cliente que se comunica con una aplicación de servidor que no es MFC para la que no tiene acceso al código fuente. En este escenario, debe suponer que el servidor que no es MFC utiliza el orden de bytes de red estándar. En cambio, la aplicación `CArchive` cliente MFC `CSocket` utiliza `CArchive` un objeto con un objeto y usa el orden de bytes "little-Endian", lo contrario que el estándar de red.

Supongamos que el servidor que no es MFC con el que va a comunicarse tiene un protocolo establecido para un paquete de mensajes como el siguiente:

[!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_1.cpp)]

En términos MFC, esto se expresaría de la siguiente manera:

[!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_2.cpp)]

En C++, una **estructura** es esencialmente lo mismo que una clase. La `Message` estructura puede tener funciones `Serialize` miembro, como la función miembro declarada anteriormente. La `Serialize` función miembro podría tener este aspecto:

[!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_3.cpp)]

En este ejemplo se llama a las conversiones de orden de bytes de datos porque hay una `CArchive` clara discordancia entre el orden de bytes de la aplicación de servidor que no es MFC en un extremo y el utilizado en la aplicación cliente MFC en el otro extremo. En el ejemplo se muestran varias de las funciones de conversión de orden de bytes que proporciona Windows Sockets. En la tabla siguiente se describen estas funciones.

### <a name="windows-sockets-byte-order-conversion-functions"></a>Funciones de conversión de orden de bytes de Windows Sockets

|Función|Propósito|
|--------------|-------------|
|**ntohs**|Convierta una cantidad de 16 bits del orden de bytes de red en orden de bytes de host (big-Endian a little-Endian).|
|**ntohl**|Convierta una cantidad de 32 bits del orden de bytes de red en orden de bytes de host (big-Endian a little-Endian).|
|**Htons**|Convierta una cantidad de 16 bits del orden de bytes del host al orden de bytes de red (little-Endian a big-Endian).|
|**Htonl**|Convierta una cantidad de 32 bits del orden de bytes del host al orden de bytes de red (little-Endian a big-Endian).|

Otro punto de este ejemplo es que cuando la aplicación de socket en el otro extremo de la comunicación es una aplicación que no es MFC, debe evitar hacer algo como lo siguiente:

`ar << pMsg;`

donde `pMsg` es un puntero a un objeto `CObject`C++ derivado de la clase . Esto enviará información adicional de MFC asociada a objetos y el servidor no lo entenderá, como lo haría si fuera una aplicación MFC.

Para más información, consulte:

- [Windows Sockets: Usar la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Nociones](../mfc/windows-sockets-background.md)

- [Windows Sockets: Sockets de secuencias](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Sockets de datagramas](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Consulte también

[Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)
