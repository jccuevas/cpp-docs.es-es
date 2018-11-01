---
title: setjmp longjump
ms.date: 11/04/2016
ms.assetid: b0e21902-095d-4198-8f9a-b6326525721a
ms.openlocfilehash: 765cef3f02bed09bed0278aaeecdcdbd55d86b67
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50427903"
---
# <a name="setjmplongjump"></a>setjmp/longjump

Al incluir setjmpex.h o setjmp.h, todas las llamadas a [setjmp](../c-runtime-library/reference/setjmp.md) o [longjmp](../c-runtime-library/reference/longjmp.md) dará como resultado un desenredo que invoca destructores y, por último, se llama.  Esto difiere de x86, donde incluir resultados de setjmp.h en cláusulas finally y los destructores no que se va a invocar.

Una llamada a `setjmp` conserva el puntero de pila actual, registros no volátiles y registros de MxCsr.  Las llamadas a `longjmp` vuelva a la más reciente `setjmp` llamar al sitio y restablece el puntero de pila y registros no volátiles MxCsr registra, vuelve al estado mantenido desde la última `setjmp` llamar.

## <a name="see-also"></a>Vea también

[Convención de llamada](../build/calling-convention.md)