---
title: Compilador advertencia (nivel 1) C4076 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4076
dev_langs: C++
helpviewer_keywords: C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9b361448f7181ed4fd044ec18a7b36c4f86012fb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4076"></a>Advertencia del compilador (nivel 1) C4076
'typemod': no se puede utilizar con el tipo 'typename'  
  
 Un modificador de tipo, tanto si es **signed** como `unsigned`, no se puede usar con un tipo no entero. ***typemod*** se omite.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C4076:  
  
```  
// C4076.cpp  
// compile with: /W1 /LD  
unsigned double x;   // C4076  
```