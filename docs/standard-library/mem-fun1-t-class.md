---
title: Clase mem_fun1_t | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xfunctional/std::mem_fun1_t
dev_langs: C++
helpviewer_keywords: mem_fun1_t class
ms.assetid: 01a8c2c2-b2f7-4e3f-869c-5b5b9f06ea54
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: db6449ad7cb350eddaa0abeecd9463fc53407d4a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="memfun1t-class"></a>mem_fun1_t (Clase)
Clase de adaptadores que permite llamar a una función miembro **non_const** que toma un solo argumento como un objeto de función binaria cuando se inicializa con un argumento de puntero.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Result, class Type, class Arg>
class mem_fun1_t : public binary_function<Type *, Arg, Result> {
    explicit mem_fun1_t(
    Result (Type::* _Pm)(Arg));

    Result operator()(
    Type* _Pleft,
    Arg right) const;

 };
```  
  
#### <a name="parameters"></a>Parámetros  
 `_Pm`  
 Un puntero a la función miembro de clase **Type** que se convertirá en un objeto de función.  
  
 `_Pleft`  
 El objeto en que se llama a la función miembro `_Pm`.  
  
 `right`  
 El argumento que se entrega a `_Pm`.  
  
## <a name="return-value"></a>Valor devuelto  
 Una función binaria adaptable.  
  
## <a name="remarks"></a>Comentarios  
 La clase de plantilla almacena una copia de `_Pm`, que debe ser un puntero a una función miembro de clase **Type**, en un objeto miembro privado. Define su función miembro `operator()` para que devuelva ( **_Pleft**->\* `_Pm`)( **right**).  
  
## <a name="example"></a>Ejemplo  
  Normalmente, no se usa el constructor de `mem_fun1_t` directamente; la función auxiliar `mem_fun` se usa para adaptar funciones miembro. Vea [mem_fun](../standard-library/functional-functions.md#mem_fun) para obtener un ejemplo de cómo usar adaptadores de funciones miembro.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<functional>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)


