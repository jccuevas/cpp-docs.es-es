---
title: IConvertTypeImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IConvertTypeImpl<T>
- IConvertTypeImpl
- ATL.IConvertTypeImpl
- ATL::IConvertTypeImpl
- ATL::IConvertTypeImpl<T>
- IConvertTypeImpl.CanConvert
- CanConvert
- IConvertTypeImpl::CanConvert
dev_langs:
- C++
helpviewer_keywords:
- IConvertTypeImpl class
- CanConvert method
ms.assetid: 7f81e79e-7d3f-4cbe-b93c-d632a94b15f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 57ad4c5e9f119a7c9904376db4f77c35de4290f2
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337133"
---
# <a name="iconverttypeimpl-class"></a>IConvertTypeImpl (Clase)
Proporciona una implementación de la [IConvertType](https://msdn.microsoft.com/library/ms715926.aspx) interfaz.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class T>  
class ATL_NO_VTABLE IConvertTypeImpl   
   : public IConvertType, public CConvertHelper  
```  
  
### <a name="parameters"></a>Parámetros  
 *T*  
 La clase derivada de `IConvertTypeImpl`.  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="members"></a>Miembros  
  
### <a name="interface-methods"></a>Métodos de interfaz  
  
|||  
|-|-|  
|[CanConvert](#canconvert)|Proporciona información sobre la disponibilidad de las conversiones de tipos en un comando o en un conjunto de filas.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz es obligatoria en los comandos, los conjuntos de filas y conjuntos de filas de índice. `IConvertTypeImpl` implementa la interfaz mediante la delegación para el objeto de conversión proporcionado por OLE DB.  

## <a name="canconvert"></a> Iconverttypeimpl:: CanConvert
Proporciona información sobre la disponibilidad de las conversiones de tipos en un comando o en un conjunto de filas.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
STDMETHOD(CanConvert)(DBTYPE wFromType,   
   DBTYPE wToType,   
   DBCONVERTFLAGS dwConvertFlags);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Consulte [IConvertType::CanConvert](https://msdn.microsoft.com/library/ms711224.aspx) en el *referencia del programador OLE DB*.  
  
### <a name="remarks"></a>Comentarios  
 Utiliza la conversión de datos OLE DB en `MSADC.DLL`.  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)