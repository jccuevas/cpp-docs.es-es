---
title: Error grave de NMAKE U1099 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1099
dev_langs:
- C++
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7be09691de4212d07b1452ffe33725a3978fc053
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-fatal-error-u1099"></a>Error grave de NMAKE U1099
desbordamiento de pila  
  
 El archivo MAKE procesando era demasiado complejo para la asignación de pila actual en NMAKE. NMAKE tiene una asignación de 0 x 3000 (12 KB).  
  
 Para aumentar la asignación de pila de NMAKE, ejecute la [editbin /stack](../../build/reference/stack.md) utilidad con una opción de pila superior:  
  
 **EDITBIN /STACK:reserve NMAKE. EXE**  
  
 donde *reservar* es un número mayor que la asignación de pila actual de NMAKE.