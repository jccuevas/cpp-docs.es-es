---
title: alloca | Microsoft Docs
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
ms.openlocfilehash: e0c73abcb52b991ee6bd4de839861aa4ef684181
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702751"
---
# <a name="alloca"></a>alloca

[_alloca](../c-runtime-library/reference/alloca.md) debe ser 16 bytes que se alinea y además debe usar un puntero de marco.

La pila que se asigna debe incluir el espacio debajo de él para parámetros de funciones llamadas posteriormente, como se describe en [asignación de pila](../build/stack-allocation.md).

## <a name="see-also"></a>Vea también

[Uso de las pilas](../build/stack-usage.md)