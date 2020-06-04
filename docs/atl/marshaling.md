---
title: Marshaling
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
ms.openlocfilehash: 83cf29fb45347b7bfcfc1644546684f074061d25
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319348"
---
# <a name="marshaling"></a>Marshaling

La técnica COM de cálculo de referencias permite que las interfaces expuestas por un objeto en un proceso se utilicen en otro proceso. En el cálculo de referencias, COM proporciona código (o usa código proporcionado por el implementador de la interfaz) tanto para empaquetar los parámetros de un método en un formato que se puede mover a través de procesos (así como, a través de la conexión a los procesos que se ejecutan en otros equipos) y para desempaquetar esos parámetros en el otro extremo. Del mismo modo, COM debe realizar estos mismos pasos en la devolución de la llamada.

> [!NOTE]
> Normalmente, el cálculo de referencias no es necesario cuando se utiliza una interfaz proporcionada por un objeto en el mismo proceso que el objeto. Sin embargo, el cálculo de referencias puede ser necesario entre subprocesos.

## <a name="see-also"></a>Consulte también

[Introducción a COM](../atl/introduction-to-com.md)<br/>
[Detalles del cálculo de referencias](/windows/win32/com/marshaling-details)
