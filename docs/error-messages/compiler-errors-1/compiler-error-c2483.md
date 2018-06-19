---
title: Error del compilador C2483 | Documentos de Microsoft
ms.custom: ''
ms.date: 09/15/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2483
dev_langs:
- C++
helpviewer_keywords:
- C2483
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a10fd33ebeef43904db964fc327fb749029f963
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197980"
---
# <a name="compiler-error-c2483"></a>Error del compilador C2483

>'*identificador*': objeto con el constructor o destructor no se puede declarar como 'thread'

Este mensaje de error es obsoleta en Visual Studio 2015 y versiones posteriores. En versiones anteriores, las variables se declaran con la `thread` atributo no se puede inicializar con un constructor u otra expresión que requiera evaluación en tiempo de ejecución. Se requiere una expresión estática para inicializar `thread` datos.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2483 en Visual Studio 2013 y versiones anteriores.

```cpp
// C2483.cpp
// compile with: /c
__declspec(thread) struct A {
   A(){}
   ~A(){}
} aa;   // C2483 error  

__declspec(thread) struct B {} b;   // OK
```

## <a name="see-also"></a>Vea también

[thread](../../cpp/thread.md)