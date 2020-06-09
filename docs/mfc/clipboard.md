---
title: Portapapeles
ms.date: 11/04/2016
helpviewer_keywords:
- cutting and copying data
- copying data
- Clipboard
- Clipboard, programming
- transferring data
ms.assetid: a71b2824-1f14-4914-8816-54578d73ad4e
ms.openlocfilehash: 5f4a17bedaa50913dce1f6388dfb6b8d9ecd38da
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617290"
---
# <a name="clipboard"></a>Portapapeles

Esta familia de artículos explica cómo implementar la compatibilidad del portapapeles de Windows en las aplicaciones MFC. El portapapeles de Windows se utiliza de dos maneras:

- Implementar comandos del menú edición estándar, como cortar, copiar y pegar.

- Implementar la transferencia de datos uniforme con arrastrar y colocar de OLE.

El portapapeles es el método estándar de Windows para transferir datos entre un origen y un destino. También puede ser muy útil en operaciones OLE. Con la llegada de OLE, hay dos mecanismos de Portapapeles en Windows. La API del portapapeles de Windows estándar sigue estando disponible, pero se ha complementado con el mecanismo de transferencia de datos OLE. La transferencia de datos uniforme OLE (UDT) admite cortar, copiar y pegar con el portapapeles y arrastrar y colocar.

El portapapeles es un servicio del sistema compartido por la sesión de Windows completa, por lo que no tiene un identificador o una clase propia. El portapapeles se administra a través de las funciones miembro de la clase [CWnd](reference/cwnd-class.md).

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Cuándo usar cada mecanismo del portapapeles](clipboard-when-to-use-each-clipboard-mechanism.md)

- [Uso de la API tradicional del portapapeles de Windows](clipboard-using-the-windows-clipboard.md)

- [Usar el mecanismo del portapapeles OLE](clipboard-using-the-ole-clipboard-mechanism.md)

- [Copiado y pegado de datos](clipboard-copying-and-pasting-data.md)

- [Agregar otros formatos](clipboard-adding-other-formats.md)

- [El portapapeles de Windows](/windows/win32/dataxchg/clipboard)

- [Funciones OLE de arrastrar y colocar](drag-and-drop-ole.md)

## <a name="see-also"></a>Consulte también

[Elementos de la interfaz de usuario](user-interface-elements-mfc.md)
