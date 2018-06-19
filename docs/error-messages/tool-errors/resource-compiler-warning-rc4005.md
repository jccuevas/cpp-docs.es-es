---
title: Advertencia del compilador de recursos RC4005 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC4005
dev_langs:
- C++
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 724764e443d4ab999c1df1247e9f5572ebdb2078
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322489"
---
# <a name="resource-compiler-warning-rc4005"></a>Advertencia del compilador de recursos RC4005
'identificador': nueva definición de macro  
  
 El identificador se define dos veces. El compilador utilizó la segunda definición de macro.  
  
 Esta advertencia puede deberse a la definición de una macro en la línea de comandos y en el código con un `#define` directiva. También puede deberse a macros importadas de archivos de inclusión.  
  
 Para eliminar la advertencia, quite una de las definiciones o use un `#undef` Directiva antes de la segunda definición.