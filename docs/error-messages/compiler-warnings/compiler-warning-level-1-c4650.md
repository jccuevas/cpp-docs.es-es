---
title: Compilador (nivel 1) de la advertencia C4650 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4650
dev_langs:
- C++
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 449fbd2efd0d6b2b434420996d9175d643f9b7a2
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4650"></a>Advertencia del compilador (nivel 1) C4650
la información de depuración no está en el encabezado precompilado; solo estarán disponibles símbolos globales del encabezado  
  
 El archivo de encabezado precompilado no se compiló con la información de depuración simbólica de Microsoft.  
  
 Una vez vinculado, el archivo ejecutable o de vínculos dinámicos biblioteca resultante no incluirá información de depuración para los símbolos locales contenidos en el encabezado precompilado.  
  
 Esta advertencia puede evitarse volviendo a compilar el archivo de encabezado precompilado con la [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) opción de línea de comandos.
