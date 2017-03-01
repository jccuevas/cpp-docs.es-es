---
title: Struct iterator | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- iterator
- std::iterator
- std.iterator
- xutility/std::iterator
dev_langs:
- C++
helpviewer_keywords:
- iterator class
- iterator struct
ms.assetid: c74c8000-8b18-4829-9b71-6103c4229b74
caps.latest.revision: 18
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
ms.openlocfilehash: b14712f36d8cc7b4dbbdd4fd6a0cef3cb0667d8b
ms.lasthandoff: 02/24/2017

---
# <a name="iterator-struct"></a>iterator (Struct)
Struct base vacío usado para garantizar que una clase de iterador definida por el usuario funciona correctamente con **iterator_trait**.  
  
## <a name="syntax"></a>Sintaxis  
```    
struct iterator {
   typedef Category iterator_category;
   typedef Type value_type;
   typedef Distance difference_type;
   typedef Distance distance_type;
   typedef Pointer pointer;
   typedef Reference reference;
   };  
```    
## <a name="remarks"></a>Comentarios  
 El struct de plantilla se usa como tipo base para todos los iteradores. Define los tipos de miembro:  
  
- `iterator_category` (sinónimo para el parámetro de plantilla `Category`).  
  
- `value_type` (sinónimo para el parámetro de plantilla **Type**).  
  
- `difference_type` (sinónimo para el parámetro de plantilla `Distance`).  
  
- `distance_type` (sinónimo para el parámetro de plantilla `Distance`).  
  
- `pointer` (sinónimo para el parámetro de plantilla `Pointer`).  
  
- `reference` (sinónimo para el parámetro de plantilla `Reference`).  
  
 Tenga en cuenta que `value_type` no debe ser un tipo constante, incluso si **pointer** apunta a un objeto de **Type** const y la referencia designa un objeto de **Type** const.  
  
## <a name="example"></a>Ejemplo  
 Vea [iterator_traits](../standard-library/iterator-traits-struct.md) para obtener un ejemplo de cómo declarar y usar los tipos de la clase base del iterador.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<iterator>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [\<iterator>](../standard-library/iterator.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)




