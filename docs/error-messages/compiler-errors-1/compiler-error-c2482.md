---
title: Error del compilador C2482 | Documentos de Microsoft
ms.custom: 
ms.date: 09/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2482
dev_langs: C++
helpviewer_keywords: C2482
ms.assetid: 98c87da2-625c-4cc2-9bf7-78d15921e779
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c4a5d081e7a19f09f10e40e3799f724f44b295fc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
