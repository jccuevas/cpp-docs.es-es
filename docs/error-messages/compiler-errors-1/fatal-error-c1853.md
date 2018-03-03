---
title: Error irrecuperable C1853 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1853
dev_langs:
- C++
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 05c29c266aad095517734fdcac776e12467d34ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1853"></a>Error irrecuperable C1853
  
> '*filename*' archivo de encabezado precompilado es de una versión anterior del compilador, o el encabezado precompilado es de C++ y que está utilizando desde C (o viceversa)  
  
Causas posibles:  
  
-   El encabezado precompilado se compiló con una versión anterior del compilador. Intente volver a compilar el encabezado con el compilador actual.  
  
-   El encabezado precompilado es de C++ y lo está utilizando desde Try C. volver a compilar el encabezado para su uso con C especificando uno de los [/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) opciones del compilador, o cambiar el sufijo del archivo de origen a "c". Para obtener más información, consulte [dos opciones para precompilar código](../../build/reference/creating-precompiled-header-files.md#two-choices-for-precompiling-code).