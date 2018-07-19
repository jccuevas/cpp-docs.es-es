---
title: Error del evaluador de expresiones CXX0033 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0033
dev_langs:
- C++
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 720b1aec6c9be16879119bc0e8148a301507577a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299505"
---
# <a name="expression-evaluator-error-cxx0033"></a>Error del evaluador de expresiones CXX0033
Error en la información de tipo OMF  
  
 El archivo ejecutable no tenía un formato de módulo de objeto válido (OMF) para la depuración.  
  
 Este error es idéntico a CAN0033.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  El archivo ejecutable no se creó con el vinculador lanzado con esta versión de Visual C++. Volver a vincular el código de objeto con la versión actual de LINK.exe.  
  
2.  Puede que el archivo .exe que esté dañado. Volver a compilar y volver a vincular el programa.