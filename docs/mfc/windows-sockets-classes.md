---
title: Clases de Windows Sockets
ms.date: 11/04/2016
f1_keywords:
- vc.classes.net
helpviewer_keywords:
- sockets classes [MFC]
- Windows Sockets [MFC], classes
ms.assetid: 58b9ab8d-9e44-4db3-8265-e04e713d2e9a
ms.openlocfilehash: 4abdd8f8fbfc115b5014ffd0b3a37df357852b16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62371807"
---
# <a name="windows-sockets-classes"></a>Clases de Windows Sockets

Windows Sockets proporciona una manera independiente del protocolo de red para la comunicación entre dos equipos. Estos sockets pueden ser sincrónicos (el programa espera hasta que la comunicación se realiza) o asincrónica (el programa continúa ejecutándose mientras la comunicación está ocurriendo).

[CAsyncSocket](../mfc/reference/casyncsocket-class.md)<br/>
Encapsula la API de Windows Sockets en un contenedor fino.

[CSocket](../mfc/reference/csocket-class.md)<br/>
Deriva de mayor nivel de abstracción `CAsyncSocket`. Opera de forma sincrónica.

[CSocketFile](../mfc/reference/csocketfile-class.md)<br/>
Proporciona un `CFile` interfaz a un Socket de Windows.

## <a name="see-also"></a>Vea también

[Información general de clases](../mfc/class-library-overview.md)
