---
title: Compilador advertencia (nivel 1) C4124 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4124
dev_langs: C++
helpviewer_keywords: C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3de13cb50444530fc0917330771b693f60a7e5f5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4124"></a>Compilador advertencia (nivel 1) C4124
__fastcall con comprobación de pila es ineficaz  
  
 El `__fastcall` palabra clave se usó con comprobación de pila habilitada.  
  
 El `__fastcall` convención genera código más rápido, pero la comprobación de pila hace el código más lento. Cuando se usa `__fastcall`, desactive la opción de comprobación de la pila con la **check_stack** pragma o/GS..  
  
 Esta advertencia se emite solo para la primera función declarada en estas condiciones.