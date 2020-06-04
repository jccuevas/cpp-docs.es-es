---
title: Clases de Windows Sockets
ms.date: 11/04/2016
helpviewer_keywords:
- sockets classes [MFC]
- Windows Sockets [MFC], classes
ms.assetid: 58b9ab8d-9e44-4db3-8265-e04e713d2e9a
ms.openlocfilehash: 3f1b7b2b6674b4a5f8c8f7bff6c5fa239715f459
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445985"
---
# <a name="windows-sockets-classes"></a>Clases de Windows Sockets

Windows Sockets proporciona una manera independiente del Protocolo de red de comunicarse entre dos equipos. Estos Sockets pueden ser sincrónicos (el programa espera hasta que se realiza la comunicación) o asincrónicos (el programa continúa ejecutándose mientras la comunicación está en curso).

[CAsyncSocket](../mfc/reference/casyncsocket-class.md)<br/>
Encapsula la API de Windows Sockets en un contenedor fino.

[CSocket](../mfc/reference/csocket-class.md)<br/>
Abstracción de nivel superior derivada de `CAsyncSocket`. Funciona de forma sincrónica.

[CSocketFile](../mfc/reference/csocketfile-class.md)<br/>
Proporciona una interfaz de `CFile` a un socket de Windows.

## <a name="see-also"></a>Consulte también

[Información general sobre clases](../mfc/class-library-overview.md)
