---
title: Advertencia del compilador (nivel 4) C4718
ms.date: 11/04/2016
f1_keywords:
- C4718
helpviewer_keywords:
- C4718
ms.assetid: 29507f8a-b024-42c1-a3b8-f35d1f2641f3
ms.openlocfilehash: c313e26af5f5b17db9c7d001a705ff7211461c2b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395175"
---
# <a name="compiler-warning-level-4-c4718"></a>Advertencia del compilador (nivel 4) C4718

'llamada a función': la llamada recursiva no tiene efectos secundarios; se eliminará

Una función contiene una llamada recursiva, pero no tiene efectos secundarios. Se está eliminando una llamada a esta función. La precisión del programa no se ve afectada, pero sí el comportamiento. Dado que si se deja la llamada entrante podría producirse una excepción de desbordamiento de pila en tiempo de ejecución, la eliminación de la llamada evita esa posibilidad.