---
title: nothrow_t (Estructura) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: nothrow_t
dev_langs: C++
helpviewer_keywords: nothrow_t class
ms.assetid: dc7d5d42-ed5a-4919-88fe-bbad519b7a1d
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9975df6ca866ce45a0e4859d19c6cfd6f3f96db2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="nothrowt-structure"></a>nothrow_t (Estructura)
El struct que se usa como parámetro de función del operador new para indicar que la función debe devolver un puntero nulo para notificar un error de asignación, en lugar de producir una excepción.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct std::nothrow_t {};
```  
  
## <a name="remarks"></a>Comentarios  
 El struct ayuda al compilador a seleccionar la versión correcta del constructor. [nothrow](../standard-library/new-functions.md#nothrow) es un sinónimo de objetos de tipo `std::nothrow_t`.  
  
## <a name="example"></a>Ejemplo  
 Vea [operator new](../standard-library/new-operators.md#op_new) y [operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr) para obtener ejemplos de cómo se usa `std::nothrow_t` como un parámetro de función.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<new>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



