---
title: "Abort (función) | Documentos de Microsoft"
ms.custom: 
ms.date: 12/01/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- abort function
ms.assetid: 3352bcc4-1a8a-4e1f-8dcc-fe30f6b50f2d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e73c2549e5ce29823376b378b9dc565e2d883ffa
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="abort-function"></a>abort (Función)

El **anular** función, también se declaran en el archivo de inclusión estándar \<stdlib.h >, finaliza un programa de C++. La diferencia entre **salir** y **anular** es que **salir** permite el procesamiento de finalización de tiempo de ejecución de C++ que se realicen (objetos globales se llamará a los destructores), mientras que **anular** finaliza el programa inmediatamente. Para obtener más información, consulte [anular](../c-runtime-library/reference/abort.md) en el *referencia de la biblioteca de tiempo de ejecución*.

## <a name="see-also"></a>Vea también

[Finalización del programa](../cpp/program-termination.md)