---
title: alloca | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 2b209335-e3a0-4934-93f0-3b5925d22918
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2f58d0c959008196798087d139b44715a67f567b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="alloca"></a>alloca
[_alloca](../c-runtime-library/reference/alloca.md) debe ser 16 bytes alineados y además debe usar un puntero de marco.  
  
 La pila que se asigna debe incluir el espacio por debajo de él para parámetros de funciones llamadas posteriormente, como se describe en [asignación de la pila](../build/stack-allocation.md).  
  
## <a name="see-also"></a>Vea también  
 [Uso de las pilas](../build/stack-usage.md)