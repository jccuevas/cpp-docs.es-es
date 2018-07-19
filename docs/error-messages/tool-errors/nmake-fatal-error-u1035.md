---
title: Error grave de NMAKE U1035 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1035
dev_langs:
- C++
helpviewer_keywords:
- U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6bb32f815345b933ad6a65a0c8c1ec8ad59cbe81
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322801"
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