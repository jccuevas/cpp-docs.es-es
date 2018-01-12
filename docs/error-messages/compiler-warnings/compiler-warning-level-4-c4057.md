---
title: Compilador advertencia (nivel 4) C4057 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4057
dev_langs: C++
helpviewer_keywords: C4057
ms.assetid: e75d0645-84c9-4bef-a812-942ed9879aa3
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1c9ef5041d26e2e5a8933a53d4f6f0153c7106cc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4057"></a>Advertencia del compilador (nivel 4) C4057
'operador': direccionamiento indirecto de 'identificador1' a tipos base ligeramente distintos de 'identificador2'.  
  
 Dos expresiones de puntero hacen referencia a diferentes tipos base. Las expresiones se usan sin conversión.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  Combinación de tipos con signo y sin signo.  
  
2.  Combinación de tipos **short** y **long** .