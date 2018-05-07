---
title: Compilador advertencia (nivel 1) C4650 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4650
dev_langs:
- C++
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6cb1c9979141e7958b6c2802aaf321efe41e9570
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4650"></a>Advertencia del compilador (nivel 1) C4650
información de depuración no está en el encabezado precompilado; solo los símbolos globales del encabezado estará disponibles  
  
 El archivo de encabezado precompilado no se compiló con información de depuración simbólica de Microsoft.  
  
 Cuando están vinculados, el archivo de biblioteca de vínculos dinámicos o ejecutable resultante no incluirá información de depuración para los símbolos locales contenidos en el encabezado precompilado.  
  
 Esta advertencia puede evitarse volviendo a compilar el archivo de encabezado precompilado con la [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) opción de línea de comandos.