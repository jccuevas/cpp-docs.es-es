---
title: Compilador Error C2719 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2719
dev_langs:
- C++
helpviewer_keywords:
- C2719
ms.assetid: ea6236d3-8286-45cc-9478-c84ad3dd3c8e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ee8779db363c506d2f4ad884e15f78ba8231caa7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33233339"
---
# <a name="compiler-error-c2719"></a>C2719 de Error del compilador
'parameter': el parámetro formal con __declspec(align('#')) no se alineará  
  
 El [alinear](../../cpp/align-cpp.md) `__declspec` modificador no está permitido en parámetros de función. La alineación de los parámetros de función se controla mediante la convención de llamada que se utiliza. Para obtener más información, consulte [convenciones de llamada](../../cpp/calling-conventions.md).  
  
 El siguiente ejemplo genera el error C2719 y muestra cómo corregirlo:  
  
```  
// C2719.cpp  
void func(int __declspec(align(32)) i);   // C2719  
// try the following line instead  
// void func(int i);  
```