---
title: const_mem_fun1_ref_t (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xfunctional/std::const_mem_fun1_ref_t
dev_langs: C++
helpviewer_keywords: const_mem_fun1_ref_t class
ms.assetid: 8220d373-fa1c-44be-a21d-96d49b3ea6bb
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d95b81ca5618cabd32af90836a67f29bf9b1923b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="constmemfun1reft-class"></a>const_mem_fun1_ref_t (Clase)
Clase de adaptadores que permite llamar a una función miembro **const** que toma un solo argumento como un objeto de función binaria cuando se inicializa con un argumento de referencia.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Result, class Type, class Arg>
class const_mem_fun1_ref_t
 : public binary_function<Type, Arg, Result> 
 {
    explicit const_mem_fun1_ref_t(Result (Type::* Pm)(Arg) const);
    Result operator()(const Type& left, Arg right) const;
 };
```  
  
#### <a name="parameters"></a>Parámetros  
 `Pm`  
 Un puntero a la función miembro de clase **Type** que se convertirá en un objeto de función.  
  
 `left`  
 El objeto **const** en que se llama a la función miembro `Pm`.  
  
 `right`  
 El argumento que se entrega a `Pm`.  
  
## <a name="return-value"></a>Valor devuelto  
 Una función binaria adaptable.  
  
## <a name="remarks"></a>Comentarios  
 La clase de plantilla almacena una copia de `Pm`, que debe ser un puntero a una función miembro de clase **Type**, en un objeto miembro privado. Define su función miembro `operator()` para que devuelva ( `left`.\* *Pm*)( `right`) **const**.  
  
## <a name="example"></a>Ejemplo  
 Normalmente, no se usa el constructor de `const_mem_fun1_ref_t` directamente; la función auxiliar `mem_fun_ref` se usa para adaptar funciones miembro. Vea [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref) para obtener ejemplos de cómo usar adaptadores de funciones miembro.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<functional>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)



