---
title: Error irrecuperable C1081
ms.date: 11/04/2016
f1_keywords:
- C1081
helpviewer_keywords:
- C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
ms.openlocfilehash: f3c9f9bde5da7fb120accbb9a8d72e5715ab9d2b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62229424"
---
# <a name="fatal-error-c1081"></a>Error irrecuperable C1081

'símbolo': nombre de archivo demasiado largo

Supera la longitud de una ruta de acceso de archivo `_MAX_PATH` (definida en STDLIB.h como de 260 caracteres). Acorte el nombre del archivo.

Si se llama a CL.exe con un nombre de archivo corto, el compilador puede necesitar generar una ruta de acceso completa. Por ejemplo, `cl -c myfile.cpp` puede hacer que el compilador generar:

```
D:\<very-long-directory-path>\myfile.cpp
```