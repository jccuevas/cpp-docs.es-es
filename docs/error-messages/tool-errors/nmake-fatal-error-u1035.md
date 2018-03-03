---
title: Error grave de NMAKE U1035 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- U1035
dev_langs:
- C++
helpviewer_keywords:
- U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0d7730f882b40c24822cb4b8e2c6a12147cacf2d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1035"></a>Error grave de NMAKE U1035
error de sintaxis: se esperaba ':' o '=' separador  
  
 Dos puntos (**:**) o un signo igual (**=**) se esperaba.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  Un destino no iba seguido de dos puntos.  
  
2.  Un coma y sin espacio (por ejemplo, a:) habían seguido de un destino de letra única. NMAKE lo ha interpretado como una especificación de unidad.  
  
3.  Una regla de inferencia no iba seguido de dos puntos.  
  
4.  Una definición de macro no iba seguida de un signo igual.  
  
5.  Un carácter seguido de una barra diagonal inversa (**\\**) que se usó para continuar un comando en una nueva línea.  
  
6.  Una cadena parecía que no siguiera cualquier regla de sintaxis NMAKE.  
  
7.  El archivo MAKE se da formato a un procesador de textos.