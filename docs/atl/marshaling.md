---
title: "El cálculo de referencias | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ec8c85606f0f0ef3de67a61181ead6537fde179e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="marshaling"></a>el cálculo de referencias
La técnica de COM de la serialización permite interfaces expuestas por un objeto en un proceso para su uso en otro proceso. En el cálculo de referencias, COM proporciona el código (o utiliza el código proporcionado por el implementador de la interfaz) para empaquetar los parámetros del método en un formato que se puede mover entre procesos (y, a través de la conexión a procesos que se ejecutan en otras máquinas) y para desempaquetar dichos parámetros en el otro extremo. Del mismo modo, COM debe realizar estos mismos pasos en la devolución de la llamada.  
  
> [!NOTE]
>  El cálculo de referencias normalmente no es necesario cuando se usa una interfaz proporcionada por un objeto en el mismo proceso que el objeto. Sin embargo, la serialización puede resultar necesario entre subprocesos.  
  
## <a name="see-also"></a>Vea también  
 [Introducción a COM](../atl/introduction-to-com.md)   
 [Detalles del cálculo de referencias](http://msdn.microsoft.com/library/windows/desktop/ms692621)

