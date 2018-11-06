---
title: Error irrecuperable C1067
ms.date: 11/04/2016
f1_keywords:
- C1067
helpviewer_keywords:
- C1067
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
ms.openlocfilehash: f8fe301e25d9ecb5cc67397f9537e0bbd86c0627
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595629"
---
# <a name="fatal-error-c1067"></a>Error irrecuperable C1067

límite del compilador: se superó el límite de 64K de tamaño de un tipo de registro

Este error puede producirse si un símbolo tiene un nombre representativo superior a 247 caracteres.  Para resolverlo, acorte el nombre del símbolo.

Cuando el compilador genera información de depuración, emite registros de tipo para definir tipos encontrados en el código fuente.  Por ejemplo, registros de tipo incluyen estructuras simples y listas de argumentos de funciones.  Algunos de estos registros de tipo pueden ser listas grandes.

Hay un límite de 64 KB en el tamaño de cualquier tipo de registro.  Si se supera ese límite de 64 KB, se producirá este error.

C1067 también puede producirse si hay muchos símbolos con nombres largos o si una clase, struct o unión tiene demasiados miembros.