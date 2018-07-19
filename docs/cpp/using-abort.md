---
title: Usar abort | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Abort
dev_langs:
- C++
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7231339ba4884445d7ad6b0161c6cff793c6db8a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32421853"
---
# <a name="using-abort"></a>Usar abort
Llamar a la [anular](../c-runtime-library/reference/abort.md) función provoca la finalización inmediata. Omite el proceso de destrucción normal de los objetos estáticos globales inicializados. También omite cualquier procesamiento especial especificado mediante la función `atexit`.  
  
## <a name="see-also"></a>Vea también  
 [Consideraciones de finalización adicionales](../cpp/additional-termination-considerations.md)