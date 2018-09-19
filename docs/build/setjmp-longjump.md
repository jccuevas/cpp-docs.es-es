---
title: setjmp longjump | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b0e21902-095d-4198-8f9a-b6326525721a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f53160a5deeb3ea0db111fc0aae7429b19b7cc86
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703279"
---
# <a name="setjmplongjump"></a>setjmp/longjump

Al incluir setjmpex.h o setjmp.h, todas las llamadas a [setjmp](../c-runtime-library/reference/setjmp.md) o [longjmp](../c-runtime-library/reference/longjmp.md) dará como resultado un desenredo que invoca destructores y, por último, se llama.  Esto difiere de x86, donde incluir resultados de setjmp.h en cláusulas finally y los destructores no que se va a invocar.

Una llamada a `setjmp` conserva el puntero de pila actual, registros no volátiles y registros de MxCsr.  Las llamadas a `longjmp` vuelva a la más reciente `setjmp` llamar al sitio y restablece el puntero de pila y registros no volátiles MxCsr registra, vuelve al estado mantenido desde la última `setjmp` llamar.

## <a name="see-also"></a>Vea también

[Convención de llamada](../build/calling-convention.md)