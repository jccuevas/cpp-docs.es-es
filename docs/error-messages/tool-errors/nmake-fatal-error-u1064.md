---
title: Error grave de NMAKE U1064 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1064
dev_langs:
- C++
helpviewer_keywords:
- U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5573943fc2c274d48768933a634b2c052361a8f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-fatal-error-u1064"></a>Error grave de NMAKE U1064
Archivo MAKE no se encuentra y se especificó ningún destino  
  
 La línea de comandos NMAKE no ha especificado un archivo MAKE o un destino y el directorio actual no contiene un archivo denominado MAKE.  
  
 NMAKE requiere un archivo MAKE o un destino de línea de comandos (o ambos). Para poner a disposición de NMAKE un archivo MAKE, especifique la opción/f o bien coloque un archivo denominado MAKE en el directorio actual. NMAKE puede crear un destino de línea de comandos mediante una regla de inferencia si no se proporciona un archivo MAKE.