---
title: Error de compilador Error C2720 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2720
dev_langs: C++
helpviewer_keywords: C2720
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 10c273d2c39d81397584ce674187057131542e89
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2720"></a>Error C2720 de Error del compilador  
  
> '*identificador*': '*especificador*' especificador de clase de almacenamiento no es válido para miembros  
  
La clase de almacenamiento no se puede usar en los miembros de clase externos a la declaración. Para corregir este error, quite el innecesarios [clase de almacenamiento](../../cpp/storage-classes-cpp.md) especificador de la definición del miembro fuera de la declaración de clase.  
  
## <a name="example"></a>Ejemplo  
  
El ejemplo siguiente genera el error C2720 y muestra cómo corregirlo:  
  
```cpp  
// C2720.cpp  
struct S {  
   static int i;  
};  
static S::i;   // C2720 - remove the unneeded 'static' to fix it  
```