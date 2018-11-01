---
title: Advertencia del compilador (nivel 1) C4829
ms.date: 11/04/2016
f1_keywords:
- C4829
helpviewer_keywords:
- C4829
ms.assetid: 4ffabe2b-2ddc-4c52-8564-d1355c93cfa6
ms.openlocfilehash: ace409cee05650e0dbfbcdd32cd15e85f8dbf006
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594173"
---
# <a name="compiler-warning-level-1-c4829"></a>Advertencia del compilador (nivel 1) C4829

Parámetros posiblemente incorrectos para la función main. Considere la posibilidad de ' intmain (Platform:: Array\<Platform:: String ^ > ^ argv)'

Algunas funciones, como main, no pueden tomar parámetros de tipo de referencia. La compilación se realizará correctamente, pero la imagen resultante probablemente no se ejecutará.

El siguiente ejemplo genera el error C4829:

```
// C4829.cpp
// compile by using: cl /EHsc /ZW /W4 /c C4829.cpp
int main(Platform::String ^ s) {}   // C4829

```