---
title: Clases de Windows Sockets
ms.date: 11/04/2016
f1_keywords:
- vc.classes.net
helpviewer_keywords:
- sockets classes [MFC]
- Windows Sockets [MFC], classes
ms.assetid: 58b9ab8d-9e44-4db3-8265-e04e713d2e9a
ms.openlocfilehash: 18537c0de09185c8cd219e3d17ef8bb297e1d711
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50433610"
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

