---
title: CAccessor (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL.CAccessor<T>
- ATL::CAccessor
- CAccessor
- ATL::CAccessor<T>
- ATL.CAccessor
helpviewer_keywords:
- CAccessor class
ms.assetid: b2ba959f-a686-46f3-8837-176248aef748
ms.openlocfilehash: cfc91f971fc975bcdd2c8ae37d798ff2f5a1cab0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62283977"
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