---
title: Clase scoped_d3d_access_lock | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 0ad333e6-9839-4736-a722-16d95d70c4b1
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
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
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: c5bc6183b3abc7a5598159717b0dbfa1dae2a05d
ms.lasthandoff: 02/24/2017

---
# <a name="scopedd3daccesslock-class"></a>scoped_d3d_access_lock (Clase)
Contenedor RAII para un bloqueo de acceso de D3D en un objeto accelerator_view.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
class scoped_d3d_access_lock;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Constructor scoped_d3d_access_lock](#ctor)|Sobrecargado. Construye un objeto `scoped_d3d_access_lock`. El bloqueo se libera cuando este objeto se sale del ámbito.|  
|[~ scoped_d3d_access_lock (destructor)](#dtor)|Libera el bloqueo acceso D3D asociado `accelerator_view` objeto.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[operador = (operador)](#operator_eq)|Toma posesión de un bloqueo de otro `scoped_d3d_access_lock`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `scoped_d3d_access_lock`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amprt.h  
  
 **Namespace:** concurrency::direct3d  

##  <a name="a-namectora-scopedd3daccesslock"></a><a name="ctor"></a>scoped_d3d_access_lock 

 Construye un objeto `scoped_d3d_access_lock`. El bloqueo se libera cuando este objeto se sale del ámbito.  
 
```  
explicit scoped_d3d_access_lock(// [1] constructor  
    accelerator_view& _Av);

 
explicit scoped_d3d_access_lock(// [2] constructor  
    accelerator_view& _Av,  
    adopt_d3d_access_lock_t _T);

 
scoped_d3d_access_lock(// [3] move constructor  
    scoped_d3d_access_lock&& _Other);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Av`  
 El `accelerator_view` a adoptar el bloqueo.  
  
 `_T`  
 Objeto `adopt_d3d_access_lock_t`.  
  
 `_Other`  
 La `scoped_d3d_access_lock` objeto desde el que se va a mover un bloqueo existente.  
  
## <a name="construction"></a>Construcción  
 [1] constructor  
 Adquiere un bloqueo de acceso D3D sobre el determinado [accelerator_view](accelerator-view-class.md) objeto. Bloques de construcción hasta que se adquiere el bloqueo.  
  
 [2] constructor de  
 Adopte un bloqueo de acceso D3D desde el determinado [accelerator_view](accelerator-view-class.md) objeto.  
  
 [3] Constructor de movimiento de  
 Toma un bloqueo de acceso D3D existente desde otro `scoped_d3d_access_lock` objeto. No impide la construcción.  

  
##  <a name="a-namedtora-scopedd3daccesslock"></a><a name="dtor"></a>~ scoped_d3d_access_lock 

 Libera el bloqueo acceso D3D asociado `accelerator_view` objeto.  
  
```  
~scoped_d3d_access_lock();
```  
## <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>operador = 

Toma posesión de un bloqueo de acceso D3D desde otro `scoped_d3d_access_lock` objeto, liberar el bloqueo anterior.  
 
```  
scoped_d3d_access_lock& operator= (scoped_d3d_access_lock&& _Other);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 Accelerator_view hacia el bloqueo de acceso de D3D.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a este `scoped_accelerator_view_lock`.  

## <a name="see-also"></a>Vea también  
 [Namespace Concurrency::Direct3D](concurrency-direct3d-namespace.md)

