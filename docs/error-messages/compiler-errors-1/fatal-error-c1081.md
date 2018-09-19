---
title: Error irrecuperable C1081 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1081
dev_langs:
- C++
helpviewer_keywords:
- C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b34f2f19a0bb8770ea9292fef120c415c0fb255a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060539"
---
# <a name="fatal-error-c1081"></a>Error irrecuperable C1081

'símbolo': nombre de archivo demasiado largo

Supera la longitud de una ruta de acceso de archivo `_MAX_PATH` (definida en STDLIB.h como de 260 caracteres). Acorte el nombre del archivo.

Si se llama a CL.exe con un nombre de archivo corto, el compilador puede necesitar generar una ruta de acceso completa. Por ejemplo, `cl -c myfile.cpp` puede hacer que el compilador generar:

```
D:\<very-long-directory-path>\myfile.cpp
```