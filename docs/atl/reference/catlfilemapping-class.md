---
title: Clase CAtlFileMapping | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
dev_langs:
- C++
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 524e5d9c7cef5bcff0d72ddf1225ef79b1b26d64
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="catlfilemapping-class"></a>Clase CAtlFileMapping
Esta clase representa un archivo asignado a memoria, agregar un operador de conversión a los métodos de [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <typename T = char>  
class CAtlFileMapping : public CAtlFileMappingBase
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de datos utilizados para el operador de conversión.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlFileMapping::operator T *](#operator_t_star)|Permite la conversión implícita de `CAtlFileMapping` objetos a `T` **\***.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase agrega un operador de conversión única para permitir la conversión implícita de `CAtlFileMapping` objetos a `T` **\***. Otros miembros proporcionados por la clase base, [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)  
  
 `CAtlFileMapping`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlfile.h  
  
##  <a name="operator_t_star"></a>  CAtlFileMapping::operator T *  
 Permite la conversión implícita de `CAtlFileMapping` objetos a `T` **\***.  
  
```  
operator T*() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un `T` **\*** puntero al principio del archivo asignado a la memoria.  
  
### <a name="remarks"></a>Comentarios  
 Llamadas [CAtlFileMappingBase::GetData](../../atl/reference/catlfilemappingbase-class.md#getdata) y vuelve a interpretar el puntero devuelto como un `T` **\*** donde *T* es el tipo que se utiliza como plantilla parámetro de esta clase.  
  
## <a name="see-also"></a>Vea también  
 [Clase CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
