---
title: Error irrecuperable C1853 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- devlang-cpp
ms.topic: error-reference
f1_keywords:
- C1853
dev_langs:
- C++
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9aa6a67c13f76b0bf43159b9e9de95068102a2b1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229214"
---
# <a name="fatal-error-c1853"></a>Error irrecuperable C1853
  
> '*filename*' archivo de encabezado precompilado es de una versión anterior del compilador, o el encabezado precompilado es de C++ y que está utilizando desde C (o viceversa)  
  
Causas posibles:  
  
-   El encabezado precompilado se compiló con una versión anterior del compilador. Intente volver a compilar el encabezado con el compilador actual.  
  
-   El encabezado precompilado es de C++ y lo está utilizando desde Try C. volver a compilar el encabezado para su uso con C especificando uno de los [/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) opciones del compilador, o cambiar el sufijo del archivo de origen a "c". Para obtener más información, consulte [dos opciones para precompilar código](../../build/reference/creating-precompiled-header-files.md#two-choices-for-precompiling-code).