---
title: Error irrecuperable C1067
ms.date: 11/04/2016
f1_keywords:
- C1067
helpviewer_keywords:
- C1067
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
ms.openlocfilehash: 3b016790220d409435ff7ea53c6f48899a9e8f1c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204352"
---
# <a name="fatal-error-c1067"></a>Error irrecuperable C1067

límite del compilador: se ha superado el límite de 64 k en el tamaño de un registro de tipo

Este error puede producirse si un símbolo tiene un nombre representativo que supera los 247 caracteres.  Para resolverlo, acorte el nombre del símbolo.

Cuando el compilador genera información de depuración, emite registros de tipo para definir los tipos que se encuentran en el código fuente.  Por ejemplo, los registros de tipo incluyen estructuras simples y listas de argumentos de funciones.  Algunos de estos registros de tipo pueden ser listas grandes.

Hay un límite de 64 k en el tamaño de cualquier registro de tipo.  Si se supera ese límite de 64 KB, se producirá este error.

C1067 también se puede producir si hay muchos símbolos con nombres largos o si una clase, estructura o Unión tiene demasiados miembros.
