---
title: Error del compilador C3552
ms.date: 11/04/2016
f1_keywords:
- C3552
helpviewer_keywords:
- C3552
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
ms.openlocfilehash: 27c4707097f43266a3be57ad6dc9591ab6f34e97
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441813"
---
# <a name="compiler-error-c3552"></a>Error del compilador C3552

'typename': un tipo de valor devuelto especificado en tiempo de ejecución no puede contener 'auto'

Si usa la palabra clave `auto` como marcador de posición del tipo de valor devuelto de una función, debe facilitar un tipo de valor devuelto especificado en tiempo de ejecución. Sin embargo, no puede usar otra palabra clave `auto` para especificar el tipo de valor devuelto especificado en tiempo de ejecución. Por ejemplo, el siguiente fragmento de código genera el error C3552.

`auto myFunction->auto; // C3552`