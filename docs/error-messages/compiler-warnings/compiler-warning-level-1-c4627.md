---
title: Compilador advertencia (nivel 1) C4627 | Microsoft Docs
ms.custom: ''
ms.date: 09/09/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4627
dev_langs:
- C++
helpviewer_keywords:
- C4627
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f6be9ba8ba45adecfe5355848126dcb4b3b2fd1
ms.sourcegitcommit: 592a2f402fef502450a45571a846175cc3ab1ceb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2018
ms.locfileid: "44249625"
---
# <a name="compiler-warning-level-1-c4627"></a>Advertencia del compilador (nivel 1) C4627

> '*header_file*': omite al buscar el precompilado uso del encabezado

Si el archivo de origen actual tiene el [/Yu \(usar archivo de encabezado precompilado)](../../build/reference/yu-use-precompiled-header-file.md) establecida, la opción, a continuación, el compilador omite todo lo que en el archivo antes de que se incluye el encabezado precompilado. Advertencia **C4627** se genera en Visual Studio 2015 y versiones anteriores si *header_file* se incluye antes del archivo de encabezado precompilado, y si el encabezado precompilado no incluye también *header_file*.

## <a name="example"></a>Ejemplo

Este ejemplo muestra cómo puede producirse el error y muestra cómo corregirlo:
 
```cpp
// c4627.cpp
#include <iostream>       // C4627 - iostream not included by pch.h
#include "pch.h"          // precompiled header file that does not include iostream
// #include <iostream>    // To fix, move the iostream header include here from above
int main()
{
    std::cout << "std::cout is defined!\n";
}
```
  
## <a name="see-also"></a>Vea también

[Crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md)
