---
title: freelist (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::freelist
- allocators/stdext::freelist::pop
- allocators/stdext::freelist::push
dev_langs: C++
helpviewer_keywords:
- stdext::freelist
- stdext::freelist [C++], pop
- stdext::freelist [C++], push
ms.assetid: 8ad7e35c-4c80-4479-8ede-1a2497b06d71
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 63490ba1be2459aa31f461193c0f754ba9ec1e12
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="freelist-class"></a>freelist (Clase)
Administra una lista de bloques de memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <std::size_t Sz, class Max>  
class freelist
 : public Max
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Sz`|El número de elementos de la matriz que se van a asignar.|  
|`Max`|La clase máxima que representa el número máximo de elementos que se van a almacenar en la lista libre. La clase máxima puede ser [max_none](../standard-library/max-none-class.md), [max_unbounded](../standard-library/max-unbounded-class.md), [max_fixed_size](../standard-library/max-fixed-size-class.md) o [max_variable_size](../standard-library/max-variable-size-class.md).|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase de plantilla administra una lista de bloques de memoria de tamaño `Sz` con la longitud máxima de la lista determinada por la clase máxima pasada en `Max`.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[freelist](#freelist)|Construye un objeto de tipo `freelist`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[pop](#pop)|Quita el primer bloque de memoria de la lista libre.|  
|[push](#push)|Agrega un bloque de memoria a la lista.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<allocators>  
  
 **Espacio de nombres:** stdext  
  
##  <a name="freelist"></a>  freelist::freelist  
 Construye un objeto de tipo `freelist`.  
  
```
freelist();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="pop"></a>  freelist::pop  
 Quita el primer bloque de memoria de la lista libre.  
  
```
void *pop();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero al bloque de memoria que se ha quitado de la lista.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve `NULL` si la lista está vacía. En caso contrario, quita el primer bloque de memoria de la lista.  
  
##  <a name="push"></a>  freelist::push  
 Agrega un bloque de memoria a la lista.  
  
```
bool push(void* ptr);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`ptr`|Un puntero al bloque de memoria que se va a agregar a la lista libre.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si la función `full` de la clase máxima devuelve `false`; en caso contrario, la función `push` devuelve `false`.  
  
### <a name="remarks"></a>Comentarios  
 Si la función `full` de la clase máxima devuelve `false`, esta función miembro agrega el bloque de memoria al que apunta `ptr` en el encabezado de la lista.  
  
## <a name="see-also"></a>Vea también  
 [\<allocators>](../standard-library/allocators-header.md)



