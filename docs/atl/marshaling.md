---
title: El cálculo de referencias
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
ms.openlocfilehash: 0661a4cdde0a3a875cf27221e884f6c65b9fea55
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262403"
---
# <a name="marshaling"></a>El cálculo de referencias

La técnica de COM de la serialización permite que las interfaces expuestas por un objeto en un proceso que se usará en otro proceso. Para calcular las referencias, COM proporciona código (o utiliza el código proporcionado por el implementador de la interfaz) para empaquetar los parámetros de un método en un formato que se puede mover entre procesos (así como, por cable a procesos que se ejecutan en otros equipos) y para desempaquetar dichos parámetros en el otro extremo. Del mismo modo, COM debe realizar estos mismos pasos en el valor devuelto de la llamada.

> [!NOTE]
>  El cálculo de referencias normalmente no es necesario cuando se usa una interfaz proporcionada por un objeto en el mismo proceso que el objeto. Sin embargo, el cálculo de referencias puede ser necesarias entre subprocesos.

## <a name="see-also"></a>Vea también

[Introducción a COM](../atl/introduction-to-com.md)<br/>
[Detalles del cálculo de referencias](/windows/desktop/com/marshaling-details)
