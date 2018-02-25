---
title: Struct iterator | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xutility/std::iterator
dev_langs:
- C++
helpviewer_keywords:
- iterator class
- iterator struct
ms.assetid: c74c8000-8b18-4829-9b71-6103c4229b74
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 274d472e3f3768a67a49ed6ca074f3a126bfd0fd
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
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



