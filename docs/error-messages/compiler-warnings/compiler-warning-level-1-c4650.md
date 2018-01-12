---
title: Compilador advertencia (nivel 1) C4650 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4650
dev_langs: C++
helpviewer_keywords: C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: af10d05562c0c60c6a010e105441533362d058df
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4650"></a>Advertencia del compilador (nivel 1) C4650
información de depuración no está en el encabezado precompilado; solo los símbolos globales del encabezado estará disponibles  
  
 El archivo de encabezado precompilado no se compiló con información de depuración simbólica de Microsoft.  
  
 Cuando están vinculados, el archivo de biblioteca de vínculos dinámicos o ejecutable resultante no incluirá información de depuración para los símbolos locales contenidos en el encabezado precompilado.  
  
 Esta advertencia puede evitarse volviendo a compilar el archivo de encabezado precompilado con la [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) opción de línea de comandos.