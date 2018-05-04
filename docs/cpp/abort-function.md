---
title: Abort (función) | Documentos de Microsoft
ms.custom: ''
ms.date: 12/01/2017
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- abort function
ms.assetid: 3352bcc4-1a8a-4e1f-8dcc-fe30f6b50f2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4acfbb5a0790dec6f7b5770832cc6b09f69a28d7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="abort-function"></a>abort (Función)

El **anular** función, también se declaran en el archivo de inclusión estándar \<stdlib.h >, finaliza un programa de C++. La diferencia entre **salir** y **anular** es que **salir** permite el procesamiento de finalización de tiempo de ejecución de C++ que se realicen (objetos globales se llamará a los destructores), mientras que **anular** finaliza el programa inmediatamente. Para obtener más información, consulte [anular](../c-runtime-library/reference/abort.md) en el *referencia de la biblioteca de tiempo de ejecución*.

## <a name="see-also"></a>Vea también

[Finalización del programa](../cpp/program-termination.md)