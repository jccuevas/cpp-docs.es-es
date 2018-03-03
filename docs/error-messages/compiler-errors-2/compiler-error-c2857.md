---
title: Error del compilador C2857 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2857
dev_langs:
- C++
helpviewer_keywords:
- C2857
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c4bf637f0abb5affdb21deb8e081c8b5156afd88
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2857"></a>Error del compilador C2857
' #include ' no se encontró la instrucción especificada con la opción de línea de comandos /Ycfilename en el archivo de origen  
  
 El [/Yc](../../build/reference/yc-create-precompiled-header-file.md) opción especifica el nombre de un archivo de inclusión que no se incluye en el archivo de origen que se está compilando.  
  
 Este error puede deberse a un `#include` declaración de un bloque de compilación condicional no se compila.