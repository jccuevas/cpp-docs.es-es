---
title: Error grave de NMAKE U1099 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- U1099
dev_langs:
- C++
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8bf8d662960e5857686f3f8301cc8481f350d4b3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1099"></a>Error grave de NMAKE U1099
desbordamiento de pila  
  
 El archivo MAKE procesando era demasiado complejo para la asignación de pila actual en NMAKE. NMAKE tiene una asignación de 0 x 3000 (12 KB).  
  
 Para aumentar la asignación de pila de NMAKE, ejecute la [editbin /stack](../../build/reference/stack.md) utilidad con una opción de pila superior:  
  
 **EDITBIN /STACK:reserve NMAKE. EXE**  
  
 donde *reservar* es un número mayor que la asignación de pila actual de NMAKE.