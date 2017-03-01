---
title: Clase mem_fun_ref_t | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xfunctional/std::mem_fun_ref_t
- mem_fun_ref_t
- std.mem_fun_ref_t
- std::mem_fun_ref_t
dev_langs:
- C++
helpviewer_keywords:
- mem_fun_ref_t class
ms.assetid: 7dadcac3-8d33-4e4b-a792-81bd53d3df39
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 2d05749ba2837a3879c91886b9266de47dd2ece6
ms.openlocfilehash: 5f8be1fed655191657f3303cd76fda772b355ef4
ms.lasthandoff: 02/24/2017

---
# <a name="memfunreft-class"></a>mem_fun_ref_t (Clase)
Clase de adaptadores que permite llamar a una función miembro **non_const** que no toma ningún argumento como un objeto de función unaria cuando se inicializa con un argumento de referencia.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Result, class Type>
class mem_fun_ref_t : public unary_function<Type, Result> {
    explicit mem_fun_ref_t(
    Result (Type::* _Pm)());

    Result operator()(Type& left) const;

 };
```  
  
#### <a name="parameters"></a>Parámetros  
 `_Pm`  
 Un puntero a la función miembro de clase **Type** que se convertirá en un objeto de función.  
  
 `left`  
 El objeto en que se llama a la función miembro `_Pm`.  
  
## <a name="return-value"></a>Valor devuelto  
 Una función unaria adaptable.  
  
## <a name="remarks"></a>Comentarios  
 La clase de plantilla almacena una copia de `_Pm`, que debe ser un puntero a una función miembro de clase **Type**, en un objeto miembro privado. Define su función miembro `operator()` para que devuelva ( **left**.* `_Pm`)( ).  
  
## <a name="example"></a>Ejemplo  
  Normalmente, no se usa el constructor de `mem_fun_ref_t` directamente; la función auxiliar `mem_fun_ref` se usa para adaptar funciones miembro. Vea [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref_function) para obtener un ejemplo de cómo usar adaptadores de funciones miembro.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<functional>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)




