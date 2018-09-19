---
title: CAccessor (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CAccessor<T>
- ATL::CAccessor
- CAccessor
- ATL::CAccessor<T>
- ATL.CAccessor
dev_langs:
- C++
helpviewer_keywords:
- CAccessor class
ms.assetid: b2ba959f-a686-46f3-8837-176248aef748
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b3adc22d940e79a4f86fec45c0d0e4fc3969f1a7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071424"
---
# <a name="caccessor-class"></a>CAccessor (Clase)

Representa uno de los tipos de descriptor de acceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
template <class T>  
class CAccessor : public CAccessorBase, public T  
```  
  
### <a name="parameters"></a>Parámetros  

*T*<br/>
La clase de registro de usuario.  
  
## <a name="remarks"></a>Comentarios  

Se usa cuando un registro de forma estática se enlaza a un origen de datos. El registro contiene el búfer. Esta clase admite varios descriptores de acceso en un conjunto de filas.  
  
Use este tipo de descriptor de acceso cuando se conoce la estructura y el tipo de la base de datos.  
  
Si el descriptor de acceso contiene los campos que señalan a la memoria (como un `BSTR` o interfaz) que debe ser liberado, llame a la función miembro [CAccessorRowset:: Freerecordmemory](../../data/oledb/caccessorrowset-freerecordmemory.md) antes del siguiente registro se leyó.  
  
## <a name="requirements"></a>Requisitos  

**Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)