---
title: Advertencia del compilador (nivel 4) C4718
ms.date: 11/04/2016
f1_keywords:
- C4718
helpviewer_keywords:
- C4718
ms.assetid: 29507f8a-b024-42c1-a3b8-f35d1f2641f3
ms.openlocfilehash: c313e26af5f5b17db9c7d001a705ff7211461c2b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573705"
---
# <a name="compiler-warning-level-4-c4718"></a>Advertencia del compilador (nivel 4) C4718

'llamada a función': la llamada recursiva no tiene efectos secundarios; se eliminará

Una función contiene una llamada recursiva, pero no tiene efectos secundarios. Se está eliminando una llamada a esta función. La precisión del programa no se ve afectada, pero sí el comportamiento. Dado que si se deja la llamada entrante podría producirse una excepción de desbordamiento de pila en tiempo de ejecución, la eliminación de la llamada evita esa posibilidad.