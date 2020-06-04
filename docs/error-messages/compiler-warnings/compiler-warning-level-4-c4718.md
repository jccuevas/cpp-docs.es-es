---
title: Advertencia del compilador (nivel 4) C4718
ms.date: 11/04/2016
f1_keywords:
- C4718
helpviewer_keywords:
- C4718
ms.assetid: 29507f8a-b024-42c1-a3b8-f35d1f2641f3
ms.openlocfilehash: 48452ed53b93d7cd89daadd3f7ab3a69b453e1a1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198164"
---
# <a name="compiler-warning-level-4-c4718"></a>Advertencia del compilador (nivel 4) C4718

'llamada a función': la llamada recursiva no tiene efectos secundarios; se eliminará

Una función contiene una llamada recursiva, pero no tiene efectos secundarios. Se está eliminando una llamada a esta función. La precisión del programa no se ve afectada, pero sí el comportamiento. Dado que si se deja la llamada entrante podría producirse una excepción de desbordamiento de pila en tiempo de ejecución, la eliminación de la llamada evita esa posibilidad.
