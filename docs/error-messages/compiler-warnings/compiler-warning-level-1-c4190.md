---
title: Compilador advertencia (nivel 1) C4190 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4190
dev_langs: C++
helpviewer_keywords: C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 127eb4327826412d605f2a4a008e411880998073
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4190"></a>Compilador advertencia (nivel 1) C4190
'identificador1' tiene una vinculación C especificada, pero devuelve UDT 'identificador2' que es incompatible con C  
  
 Una función o un puntero a función tiene un tipo definido por (definido por el usuario, que es una clase, estructura, enumeración o union) como tipo de valor devuelto y `extern` vinculación "C". Está permitido si:  
  
-   Todas las llamadas a esta función tienen lugar desde C++.  
  
-   La definición de la función está en C++.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// C4190.cpp  
// compile with: /W1 /LD  
struct X  
{  
   int i;  
   X ();  
   virtual ~X ();  
};  
  
extern "C" X func ();   // C4190  
```