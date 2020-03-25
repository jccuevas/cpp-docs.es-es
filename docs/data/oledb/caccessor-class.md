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
ms.openlocfilehash: 2b30cef2baf8c13c5001e44901b984aa1293494d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212308"
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

## <a name="remarks"></a>Observaciones

Se utiliza cuando un registro se enlaza estáticamente a un origen de datos. El registro contiene el búfer. Esta clase admite varios descriptores de acceso en un conjunto de filas.

Utilice este tipo de descriptor de acceso cuando Conozca la estructura y el tipo de la base de datos.

Si el descriptor de acceso contiene campos que apuntan a la memoria (por ejemplo, un `BSTR` o una interfaz) que deben liberarse, llame a la función miembro [CAccessorRowset:: FreeRecordMemory](../../data/oledb/caccessorrowset-freerecordmemory.md) antes de que se lea el siguiente registro.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
