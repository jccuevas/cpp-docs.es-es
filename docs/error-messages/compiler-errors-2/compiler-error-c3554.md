---
title: Error del compilador C3554
ms.date: 11/04/2016
f1_keywords:
- C3554
helpviewer_keywords:
- C3554
ms.assetid: aede18d5-fefc-4da9-9b69-adfe90bfa742
ms.openlocfilehash: ecdb90e845714e046ed21cf5a200ef4548487df6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200608"
---
# <a name="compiler-error-c3554"></a>Error del compilador C3554

'decltype' no se puede combinar con ningún otro especificador de tipo

No se puede calificar la palabra clave `decltype()` con ningún especificador de tipo. Por ejemplo, el siguiente fragmento de código genera el error C3554.

```
int x;
unsigned decltype(x); // C3554
```
