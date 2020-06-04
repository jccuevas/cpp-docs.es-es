---
title: CNoAccessor (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL::CNoAccessor
- CNoAccessor
- ATL.CNoAccessor
helpviewer_keywords:
- CNoAccessor class
ms.assetid: eb669ae5-0a56-49a3-9646-c4ae6239da31
ms.openlocfilehash: c82d756690c6c2a719cb03f458c471aa44e3d5b5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211736"
---
# <a name="cnoaccessor-class"></a>CNoAccessor (Clase)

Se puede usar como un argumento de plantilla (`TAccessor`) para las clases de plantilla, como `CCommand` y `CTable`, que requieren un argumento de clase de descriptor de acceso.

## <a name="syntax"></a>Sintaxis

```cpp
class CNoAccessor
```

## <a name="remarks"></a>Observaciones

Use `CNoAccessor` como argumento de plantilla cuando no desee que la clase admita parámetros o columnas de salida.

`CNoAccessor` implementa los siguientes métodos de código auxiliar, cada uno de los cuales corresponde a otros métodos de clase de descriptor de acceso:

- `BindColumns`: enlaza columnas a los descriptores de acceso.

- `BindParameters`: enlaza los parámetros creados a las columnas.

- `Bind`: crea enlaces.

- `Close`: cierra el descriptor de acceso.

- `ReleaseAccessors`: libera los descriptores de acceso creados por la clase.

- `FreeRecordMemory`: libera cualquier columna del registro actual que se debe liberar.

- `GetColumnInfo`: obtiene información de columna del conjunto de filas abierto.

- `GetNumAccessors`: recupera el número de descriptores de acceso creados por la clase.

- `IsAutoAccessor`: devuelve true si los datos se recuperan automáticamente para el descriptor de acceso durante una operación de movimiento.

- `GetHAccessor`: recupera el identificador de descriptor de acceso de un descriptor de acceso especificado.

- `GetBuffer`: recupera el puntero al búfer del marcador.

- `NoBindOnNullRowset`: impide el enlace de datos en conjuntos de filas vacíos.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
