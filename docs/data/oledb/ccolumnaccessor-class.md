---
title: CColumnAccessor (Clase)
ms.date: 11/04/2016
f1_keywords:
- CColumnAccessor
- ATL::CColumnAccessor
- ATL.CColumnAccessor
helpviewer_keywords:
- CColumnAccessor class
ms.assetid: 6ce1e67f-6a20-490d-9326-c168b43eee7e
ms.openlocfilehash: 2a3b1dac51a8300a915a7177c36f15512b583fa0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212115"
---
# <a name="ccolumnaccessor-class"></a>CColumnAccessor (Clase)

Genera código de consumidor insertado.

## <a name="syntax"></a>Sintaxis

```cpp
class CColumnAccessor : public CAccessorBase
```

## <a name="remarks"></a>Observaciones

En el código insertado, cada columna se enlaza como un descriptor de acceso independiente. Debe tener en cuenta que esta clase se usa en el código insertado (por ejemplo, podría encontrarla durante la depuración), pero normalmente nunca tendrá que utilizarla o sus métodos directamente.

`CColumnAccessor` implementa los siguientes métodos de código auxiliar, cada uno de los cuales se corresponde en la funcionalidad de otros métodos de clase de descriptor de acceso:

- `CColumnAccessor` el constructor; crea una instancia e inicializa el objeto `CColumnAccessor`.

- `CreateAccessor` asigna memoria a las estructuras de enlace de columna e inicializa los miembros de datos de columna.

- `BindColumns` enlaza columnas a los descriptores de acceso.

- `SetParameterBuffer` asigna búferes para los parámetros.

- `AddParameter` agrega una entrada de parámetro a las estructuras de entrada de parámetros.

- `HasOutputColumns` determina si el descriptor de acceso tiene columnas de salida

- `HasParameters` determina si el descriptor de acceso tiene parámetros.

- `BindParameters` enlaza los parámetros creados a las columnas.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
