---
title: 'Windows Sockets: Puertos y direcciones de Socket'
ms.date: 11/04/2016
helpviewer_keywords:
- ports [MFC], definition
- Windows Sockets [MFC], ports
- Windows Sockets [MFC], addresses
- ports [MFC]
- addresses [MFC], socket
- sockets [MFC], addresses
- sockets [MFC], ports
ms.assetid: e050261a-9285-4f31-a1c5-6c8033af5b4a
ms.openlocfilehash: 791bf07c927e80e65e0fda79fae8a50235bc2def
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371045"
---
# <a name="windows-sockets-ports-and-socket-addresses"></a>Windows Sockets: Puertos y direcciones de Socket

En este artículo se explican los términos "puerto" y "dirección" tal como se usa con Windows Sockets.

## <a name="port"></a><a name="_core_port"></a>Puerto

Un puerto identifica un proceso único para el que se puede proporcionar un servicio. En el contexto actual, un puerto está asociado a una aplicación que admite Windows Sockets. La idea es identificar cada aplicación de Windows Sockets de forma única para que pueda tener más de una aplicación de Windows Sockets ejecutándose en un equipo al mismo tiempo.

Ciertos puertos están reservados para servicios comunes, como FTP. Debe evitar el uso de esos puertos a menos que proporcione ese tipo de servicio. La especificación de Windows Sockets detalla estos puertos reservados. El archivo WINSOCK. H también los enumera.

Para permitir que el archivo DLL de Windows Sockets seleccione un puerto utilizable para usted, pase 0 como valor de puerto. MFC selecciona un valor de puerto mayor que 1.024 decimal. Puede recuperar el valor de puerto que MFC seleccionó mediante una llamada a la [CAsyncSocket::GetSockName](../mfc/reference/casyncsocket-class.md#getsockname) función miembro.

## <a name="socket-address"></a><a name="_core_socket_address"></a>Dirección del socket

Cada objeto de socket está asociado a una dirección de protocolo de Internet (IP) en la red. Normalmente, la dirección es un nombre de equipo, como "ftp.microsoft.com", o un número punteado, como "128.56.22.8".

Cuando se intenta crear un socket, normalmente no es necesario especificar su propia dirección.

> [!NOTE]
> Es posible que el equipo tenga varias tarjetas de red (o que la aplicación se ejecute algún día en una máquina de este tipo), cada una de las cuales representa una red diferente. Si es así, es posible que deba proporcionar una dirección para especificar qué tarjeta de red utilizará el socket. Esto es seguro que es un uso avanzado y un posible problema de portabilidad.

Para más información, consulte:

- [Windows Sockets: Usar la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Usar sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: Cómo funcionan los Sockets con archivos](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets: Sockets de secuencias](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Sockets de datagramas](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Consulte también

[Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)
