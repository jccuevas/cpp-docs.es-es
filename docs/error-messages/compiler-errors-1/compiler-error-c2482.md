---
title: Error del compilador C2482 | Documentos de Microsoft
ms.custom: ''
ms.date: 09/15/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2482
dev_langs:
- C++
helpviewer_keywords:
- C2482
ms.assetid: 98c87da2-625c-4cc2-9bf7-78d15921e779
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2c4725dd357854db504272e5b8b9d88641b143d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2482"></a>Error del compilador C2482

>'*identificador*': la inicialización dinámica de datos 'thread' no permitidos

Este mensaje de error es obsoleta en Visual Studio 2015 y versiones posteriores. En versiones anteriores, las variables se declaran mediante la `thread` atributo no se puede inicializar con una expresión que requiere la evaluación de tiempo de ejecución. Se requiere una expresión estática para inicializar `thread` datos.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2482 en Visual Studio 2013 y versiones anteriores:

```cpp
// C2482.cpp
// compile with: /c
#define Thread __declspec( thread )
Thread int tls_i = tls_i;   // C2482

int j = j;   // OK in C++; C error
Thread int tls_i = sizeof( tls_i );   // Okay in C and C++
```
