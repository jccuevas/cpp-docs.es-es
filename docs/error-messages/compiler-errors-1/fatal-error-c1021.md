---
title: Error irrecuperable C1021
ms.date: 11/04/2016
f1_keywords:
- C1021
helpviewer_keywords:
- C1021
ms.assetid: e23171f4-ca6b-40c0-a913-a2edc6fa3766
ms.openlocfilehash: 35b94e6cea177121c38d06706b42437ec610c38a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383118"
---
# <a name="fatal-error-c1021"></a>Error irrecuperable C1021

comando de preprocesador 'string' no válido

`string` no es una [directiva de preprocesador](../../preprocessor/preprocessor-directives.md)válida. Para resolver el error, use un nombre de preprocesador válido para `string`.

El ejemplo siguiente genera la advertencia C1021:

```
// C1021.cpp
#BadPreProcName    // C1021 delete line
```