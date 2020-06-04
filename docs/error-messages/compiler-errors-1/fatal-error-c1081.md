---
title: Error irrecuperable C1081
ms.date: 11/04/2016
f1_keywords:
- C1081
helpviewer_keywords:
- C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
ms.openlocfilehash: b8630a26d14c68a5f1abe45bb0b8d0141d0dedbb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204196"
---
# <a name="fatal-error-c1081"></a>Error irrecuperable C1081

' Symbol ': el nombre de archivo es demasiado largo

La longitud de una ruta de acceso de archivo supera `_MAX_PATH` (definida por STDLIB. h como 260 caracteres). Acorte el nombre del archivo.

Si llama a CL. exe con un nombre de archivo corto, es posible que el compilador tenga que generar un nombre de ruta de usuario completo. Por ejemplo, `cl -c myfile.cpp` puede hacer que el compilador genere:

```
D:\<very-long-directory-path>\myfile.cpp
```
