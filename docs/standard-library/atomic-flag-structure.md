---
title: atomic_flag (Estructura) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
dev_langs:
- C++
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8774bcc4b95e2b5c0160843100405f33010b98b6
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="atomicflag-structure"></a>atomic_flag (Estructura)
Describe un objeto que establece y borra una marca `bool` de forma atómica. Las operaciones sobre marcas atómicas nunca tienen bloqueos.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct atomic_flag;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[clear](#clear)|Establece la marca almacenada en `false`.|  
|[test_and_set](#test_and_set)|Establece la marca almacenada en `true` y devuelve el valor inicial de la marca.|  
  
## <a name="remarks"></a>Comentarios  
 Se pueden pasar objetos `atomic_flag` a las funciones no miembro [atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear), [atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit), [atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set) y [atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit). Se pueden inicializar con el valor `ATOMIC_FLAG_INIT`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<atómica >  
  
 **Espacio de nombres:** std  
  
##  <a name="clear"></a>  atomic_flag::clear
 Establece la marca `bool` almacenada en `*this` en `false`, dentro de las restricciones [memory_order](../standard-library/atomic-enums.md#memory_order_enum) especificadas.  
  
```
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```  
  
### <a name="parameters"></a>Parámetros  
 `Order`  
 [memory_order](../standard-library/atomic-enums.md#memory_order_enum).  
  
##  <a name="test_and_set"></a>  atomic_flag::test_and_set
 Establece la marca `bool` almacenada en `*this` en `true`, dentro de las restricciones [memory_order](../standard-library/atomic-enums.md#memory_order_enum) especificadas.  
  
```
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```  
  
### <a name="parameters"></a>Parámetros  
 `Order`  
 [memory_order](../standard-library/atomic-enums.md#memory_order_enum).  
  
### <a name="return-value"></a>Valor devuelto  
 Valor inicial de la marca que se almacena en `*this`.  
  
## <a name="see-also"></a>Vea también  
 [\<atomic>](../standard-library/atomic.md)



