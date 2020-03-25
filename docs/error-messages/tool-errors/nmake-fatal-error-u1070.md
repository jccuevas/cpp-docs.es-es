---
title: Error grave de NMAKE U1070
ms.date: 11/04/2016
f1_keywords:
- U1070
helpviewer_keywords:
- U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
ms.openlocfilehash: 008d49df3460cb7cf760e4b278db20da444555fe
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182778"
---
# <a name="nmake-fatal-error-u1070"></a>Error grave de NMAKE U1070

ciclo en la definición de macro ' nombremacro '

La definición de macro especificada contenía una macro cuya definición contenía la macro determinada. Las definiciones de macro circulares no son válidas.

## <a name="example"></a>Ejemplo

Las siguientes definiciones de macro

```
ONE=$(TWO)
TWO=$(ONE)
```

produce el siguiente error:

```
cycle in macro definition 'TWO'
```
