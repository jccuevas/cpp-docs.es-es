---
title: Error recuperable A2085 de ML
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2085
helpviewer_keywords:
- A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
ms.openlocfilehash: f8fdedfc1bc8bff63124d18fe1410d9f144cb926
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316842"
---
# <a name="ml-nonfatal-error-a2085"></a>Error recuperable A2085 de ML

**instrucción o registro no aceptado en el modo de CPU actual**

Se intentó usar una instrucción, un registro o una palabra clave que no era válida para el modo de procesador actual.

Por ejemplo, los registros de 32 bits requieren [. 386](dot-386.md) o superior. Los registros de control como CR0 requieren el modo privileged [. 386P](dot-386p.md) o una versión superior. Este error también se generará para las palabras clave **NEAR32**, **FAR32**y **Flat** , que requieren. **386** o superior.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](ml-error-messages.md)
