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
ms.openlocfilehash: 942a8e9eca7d09809594cbac1e4c14959aa96fbf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50632691"
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