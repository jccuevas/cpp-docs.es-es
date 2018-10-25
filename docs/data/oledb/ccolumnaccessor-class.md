---
title: CColumnAccessor (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CColumnAccessor
- ATL::CColumnAccessor
- ATL.CColumnAccessor
dev_langs:
- C++
helpviewer_keywords:
- CColumnAccessor class
ms.assetid: 6ce1e67f-6a20-490d-9326-c168b43eee7e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1e55d4c15ca5d5a3733c44cf89b788b85c905513
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50074675"
---
# <a name="ccolumnaccessor-class"></a>CColumnAccessor (Clase)

Genera código insertado de consumidor.

## <a name="syntax"></a>Sintaxis

```cpp
class CColumnAccessor : public CAccessorBase
```

## <a name="remarks"></a>Comentarios

En el código insertado, cada columna se enlaza como un descriptor de acceso independiente. Debe tener en cuenta que esta clase se usa en el código insertado (por ejemplo, es posible que aparece al depurar), pero normalmente nunca tendrá que utilizarla o sus métodos directamente.

`CColumnAccessor` implementa los siguientes métodos de código auxiliar, cada uno de los cuales corresponden de funcionalidad a otros métodos de clase de descriptor de acceso:

- `CColumnAccessor` El constructor; crea una instancia e inicializa el `CColumnAccessor` objeto.

- `CreateAccessor` Asigna memoria para la columna de las estructuras de enlace e inicializa a los miembros de datos de columna.

- `BindColumns` Enlaza las columnas a los descriptores de acceso.

- `SetParameterBuffer` Asigna los búferes de parámetros.

- `AddParameter` Agrega una entrada de parámetro a las estructuras de entrada de parámetro.

- `HasOutputColumns` Determina si el descriptor de acceso tiene columnas de salida

- `HasParameters` Determina si el descriptor de acceso tiene parámetros.

- `BindParameters` Enlaza los parámetros creados para las columnas.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="see-also"></a>Vea también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)