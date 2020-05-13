---
title: ADVERTENCIA del compilador C4746
ms.date: 11/04/2016
f1_keywords:
- C4746
helpviewer_keywords:
- C4746
ms.assetid: 5e79ab46-6031-499a-a986-716c866b6c0e
ms.openlocfilehash: 7179e2e6d4ec44355e7338ffc4e9ba36f5de47e4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165111"
---
# <a name="compiler-warning-c4746"></a>ADVERTENCIA del compilador C4746

el acceso volátil de '\<Expression > ' está sujeto a la configuración/volatile&#124;: [ISO ms]; considere la posibilidad de usar funciones intrínsecas __iso_volatile_load/Store.

Se emite C4746 siempre que se tiene acceso directo a una variable volátil. Está diseñada para ayudar a los desarrolladores a identificar ubicaciones de código que se ven afectadas por el modelo volátil específico especificado actualmente (que se puede controlar con la opción del compilador [/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md) ). En concreto, puede ser útil para buscar barreras de memoria de hardware generadas por el compilador cuando se usa/volatile: MS.

Los intrínsecos de __iso_volatile_load/Store se pueden usar para acceder explícitamente a la memoria volátil sin que se vea afectado por el modelo volátil. El uso de estos intrínsecos no desencadenará C4746.

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.
