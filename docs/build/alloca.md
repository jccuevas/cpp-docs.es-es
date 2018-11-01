---
title: alloca
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 2b209335-e3a0-4934-93f0-3b5925d22918
ms.openlocfilehash: 2c528a9cdecc52afa1e7d59f58160b247cecfee2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491629"
---
# <a name="alloca"></a>alloca

[_alloca](../c-runtime-library/reference/alloca.md) debe ser 16 bytes que se alinea y además debe usar un puntero de marco.

La pila que se asigna debe incluir el espacio debajo de él para parámetros de funciones llamadas posteriormente, como se describe en [asignación de pila](../build/stack-allocation.md).

## <a name="see-also"></a>Vea también

[Uso de las pilas](../build/stack-usage.md)