---
title: "Abort (función) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Abort
dev_langs:
- C++
helpviewer_keywords:
- abort function
ms.assetid: 3352bcc4-1a8a-4e1f-8dcc-fe30f6b50f2d
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 169c76f4925dd02aeffbaa510526ce3caa53e93f
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="abort-function"></a>abort (Función)
El **anular** función, también se declaran en el archivo de inclusión estándar STDLIB. H, se finaliza un programa de C++. La diferencia entre **salir** y **anular** es que **salir** permite el procesamiento de finalización de tiempo de ejecución de C++ que se realicen (objetos globales se llamará a los destructores), mientras que **anular** finaliza el programa inmediatamente. Para obtener más información, consulte [anular](../c-runtime-library/reference/abort.md) en el *referencia de la biblioteca de tiempo de ejecución*.  
  
## <a name="see-also"></a>Vea también  
 [Finalización del programa](../cpp/program-termination.md)
