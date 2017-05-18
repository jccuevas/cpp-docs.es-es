---
title: const_mem_fun_ref_t (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- const_mem_fun_ref_t
- xfunctional/std::const_mem_fun_ref_t
dev_langs:
- C++
helpviewer_keywords:
- const_mem_fun_ref_t class
ms.assetid: 316ddbaa-9f46-4931-8eba-ea4ca66360ef
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: f156aeb90b3569aa1fd65f06b520f294f0869541
ms.contentlocale: es-es
ms.lasthandoff: 04/19/2017

---
# <a name="constmemfunreft-class"></a>const_mem_fun_ref_t (Clase)
Clase de adaptadores que permite llamar a una función miembro **const** que no toma ningún argumento como un objeto de función unaria cuando se inicializa con un argumento de referencia.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Result, class Type>
class const_mem_fun_ref_t
 : public unary_function<Type, Result>  
{
    explicit const_mem_fun_t(Result (Type::* Pm)() const);
    Result operator()(const Type& left) const;
 };
```  
  
#### <a name="parameters"></a>Parámetros  
 `Pm`  
 Un puntero a la función miembro de clase **Type** que se convertirá en un objeto de función.  
  
 `left`  
 El objeto en que se llama a la función miembro `Pm`.  
  
## <a name="return-value"></a>Valor devuelto  
 Una función unaria adaptable.  
  
## <a name="remarks"></a>Comentarios  
 La clase de plantilla almacena una copia de `Pm`, que debe ser un puntero a una función miembro de clase **Type**, en un objeto miembro privado. Define su función miembro `operator()` para que devuelva ( **left**.\* `Pm`)() **const**.  
  
## <a name="example"></a>Ejemplo  
 Normalmente, no se usa el constructor de `const_mem_fun_ref_t` directamente; la función auxiliar `mem_fun_ref` se usa para adaptar funciones miembro. Vea [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref) para obtener un ejemplo de cómo usar adaptadores de funciones miembro.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<functional>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)




