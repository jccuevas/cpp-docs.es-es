---
title: Error del compilador C3552 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3552
dev_langs:
- C++
helpviewer_keywords:
- C3552
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a5f1453a6175019ad7c90471330d11c77da26134
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3552"></a>Error del compilador C3552
'typename': un tipo de valor devuelto especificado en tiempo de ejecución no puede contener 'auto'  
  
 Si usa la palabra clave `auto` como marcador de posición del tipo de valor devuelto de una función, debe facilitar un tipo de valor devuelto especificado en tiempo de ejecución. Sin embargo, no puede usar otra palabra clave `auto` para especificar el tipo de valor devuelto especificado en tiempo de ejecución. Por ejemplo, el siguiente fragmento de código genera el error C3552.  
  
 `auto myFunction->auto; // C3552`