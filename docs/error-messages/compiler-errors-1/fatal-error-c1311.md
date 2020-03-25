---
title: Error irrecuperable C1311
ms.date: 11/04/2016
f1_keywords:
- C1311
helpviewer_keywords:
- C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
ms.openlocfilehash: e57e4e0899a5f9d81e87a203b1b699cef0884f0d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203273"
---
# <a name="fatal-error-c1311"></a>Error irrecuperable C1311

El formato COFF no puede inicializar estáticamente ' var ' con el número de bytes de una dirección

Una dirección cuyo valor no se conoce en tiempo de compilación no se puede asignar estáticamente a una variable cuyo tipo tiene almacenamiento de menos de cuatro bytes.

Este error puede producirse en código que, de C++lo contrario, es válido.

En el ejemplo siguiente se muestra una condición que puede provocar C1311.

```
char c = (char)"Hello, world";   // C1311
char *d = (char*)"Hello, world";   // OK
```
