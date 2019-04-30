---
title: Error irrecuperable C1311
ms.date: 11/04/2016
f1_keywords:
- C1311
helpviewer_keywords:
- C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
ms.openlocfilehash: ba2b797c9bf521533e7c2ccff8d358b6216d392f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266471"
---
# <a name="fatal-error-c1311"></a>Error irrecuperable C1311

El formato COFF no puede inicializar estáticamente 'var' con número bytes de una dirección

Una dirección cuyo valor no se conoce en tiempo de compilación no se puede asignar estáticamente a una variable cuyo tipo tiene el almacenamiento de menos de cuatro bytes.

Este error puede producirse en el código que en caso contrario es válido de C++.

El ejemplo siguiente muestra una condición que podría causar C1311.

```
char c = (char)"Hello, world";   // C1311
char *d = (char*)"Hello, world";   // OK
```