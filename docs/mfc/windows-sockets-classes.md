---
title: Clases de Windows Sockets | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.net
dev_langs:
- C++
helpviewer_keywords:
- sockets classes [MFC]
- Windows Sockets [MFC], classes
ms.assetid: 58b9ab8d-9e44-4db3-8265-e04e713d2e9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 893fa525b04376cde0e96f280c95e6bfd1243946
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439983"
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

