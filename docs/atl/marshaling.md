---
title: Marshaling
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
ms.openlocfilehash: 9963e261f26daa57cb58e30ffc404b431d781bfa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492036"
---
# <a name="marshaling"></a>Marshaling

La técnica COM de serialización permite usar las interfaces expuestas por un objeto en un proceso en otro proceso. En el cálculo de referencias, COM proporciona código (o utiliza código proporcionado por el implementador de la interfaz) para empaquetar los parámetros de un método en un formato que se puede pasar por los procesos (así como, a través de la conexión a los procesos que se ejecutan en otros equipos) y desempaquetar los parámetros. en el otro extremo. Del mismo modo, COM debe realizar estos mismos pasos en la devolución de la llamada.

> [!NOTE]
>  Normalmente, no es necesario calcular las referencias cuando una interfaz proporcionada por un objeto se usa en el mismo proceso que el objeto. Sin embargo, puede que sea necesario realizar la serialización entre subprocesos.

## <a name="see-also"></a>Vea también

[Introducción a COM](../atl/introduction-to-com.md)<br/>
[Detalles de serialización](/windows/win32/com/marshaling-details)
