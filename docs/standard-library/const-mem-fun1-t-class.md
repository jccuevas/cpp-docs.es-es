---
title: const_mem_fun1_t (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std.const_mem_fun1_t
- xfunctional/std::const_mem_fun1_t
- std::const_mem_fun1_t
- const_mem_fun1_t
dev_langs:
- C++
helpviewer_keywords:
- const_mem_fun1_t class
ms.assetid: 250fac30-9663-4133-9051-6303f76ea259
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
ms.openlocfilehash: 3a2664541cd1f1a44988f81e227e553b75b4faa6
ms.lasthandoff: 02/24/2017

---
# <a name="constmemfun1t-class"></a>const_mem_fun1_t (Clase)
Clase de adaptadores que permite llamar a una función miembro **const** que toma un solo argumento como un objeto de función binaria cuando se inicializa con un argumento de puntero.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Result, class Type, class Arg>
class const_mem_fun1_t
 : public binary_function<const Type *, Arg, Result>  
{
    explicit const_mem_fun1_t(Result (Type::* _Pm)(Arg) const);
    Result operator()(const Type* _Pleft, Arg right) const;
 };
```  
  
#### <a name="parameters"></a>Parámetros  
 `_Pm`  
 Un puntero a la función miembro de clase **Type** que se convertirá en un objeto de función.  
  
 `_Pleft`  
 El objeto **const** en que se llama a la función miembro `_Pm`.  
  
 `right`  
 El argumento que se entrega a `_Pm`.  
  
## <a name="return-value"></a>Valor devuelto  
 Una función binaria adaptable.  
  
## <a name="remarks"></a>Comentarios  
 La clase de plantilla almacena una copia de `_Pm`, que debe ser un puntero a una función miembro de clase **Type**, en un objeto miembro privado. Define su función miembro `operator()` para que devuelva ( **_Pleft**->\* *Pm)(***Right**) **const**.  
  
## <a name="example"></a>Ejemplo  
 Normalmente, no se usa el constructor de `const_mem_fun1_t` directamente; la función auxiliar `mem_fun` se usa para adaptar funciones miembro. Vea [mem_fun](../standard-library/functional-functions.md#mem_fun_function) para obtener un ejemplo de cómo usar adaptadores de funciones miembro.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<functional>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)




