---
title: Error grave de NMAKE U1073 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1073
dev_langs:
- C++
helpviewer_keywords:
- U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dde9ca2f4a15edf6599dcc31b39d9411645f2a6f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33316311"
---
# <a name="nmake-fatal-error-u1073"></a>Error grave de NMAKE U1073
no sabe cómo hacer 'nombrededestino'  
  
 El destino especificado no existe y no hay ningún comando para ejecutar o que se aplique la regla de inferencia.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo  
  
1.  Compruebe la ortografía del nombre de destino.  
  
2.  Si *targetname* es un pseudodestino, especifíquelo como un destino en otro bloque de descripción.  
  
3.  Si *targetname* es una llamada de macro, asegúrese de que no se expande a una cadena nula.