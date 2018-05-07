---
title: Error del compilador C2857 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2857
dev_langs:
- C++
helpviewer_keywords:
- C2857
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4bb2ec5047646bea420bf109f18a72d87a8f7c44
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2857"></a>Error del compilador C2857
' #include ' no se encontró la instrucción especificada con la opción de línea de comandos /Ycfilename en el archivo de origen  
  
 El [/Yc](../../build/reference/yc-create-precompiled-header-file.md) opción especifica el nombre de un archivo de inclusión que no se incluye en el archivo de origen que se está compilando.  
  
 Este error puede deberse a un `#include` declaración de un bloque de compilación condicional no se compila.