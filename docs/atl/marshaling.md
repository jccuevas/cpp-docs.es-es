---
title: El cálculo de referencias | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f9e8e080837ed109a786c2123ab90624d994cd1
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753741"
---
# <a name="marshaling"></a>El cálculo de referencias

La técnica de COM de la serialización permite que las interfaces expuestas por un objeto en un proceso que se usará en otro proceso. Para calcular las referencias, COM proporciona código (o utiliza el código proporcionado por el implementador de la interfaz) para empaquetar los parámetros de un método en un formato que se puede mover entre procesos (así como, por cable a procesos que se ejecutan en otros equipos) y para desempaquetar dichos parámetros en el otro extremo. Del mismo modo, COM debe realizar estos mismos pasos en el valor devuelto de la llamada.

> [!NOTE]
>  El cálculo de referencias normalmente no es necesario cuando se usa una interfaz proporcionada por un objeto en el mismo proceso que el objeto. Sin embargo, el cálculo de referencias puede ser necesarias entre subprocesos.

## <a name="see-also"></a>Vea también

[Introducción a COM](../atl/introduction-to-com.md)   
[Detalles del cálculo de referencias](/windows/desktop/com/marshaling-details)

