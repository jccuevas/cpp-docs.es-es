---
title: Subdesbordamiento de valores de punto flotante
ms.date: 11/04/2016
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
ms.openlocfilehash: 93230b50b81ede44a9c55406db1566df2660c1ba
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344059"
---
# <a name="underflow-of-floating-point-values"></a>Subdesbordamiento de valores de punto flotante

**ANSI 4.5.1** Si las funciones matemáticas establecen la expresión de entero `errno` en el valor de la macro `ERANGE` en errores de intervalo de subdesbordamiento

Un subdesbordamiento de punto flotante no establece la expresión `errno` en `ERANGE`. Cuando un valor se aproxima a cero y finalmente sufre subdesbordamiento, el valor se establece en cero.

## <a name="see-also"></a>Vea también

[Funciones de la biblioteca](../c-language/library-functions.md)
