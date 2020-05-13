---
title: CTable (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL::CTable
- ATL.CTable
- CTable
- ATL.CTable.Open
- ATL::CTable::Open
- CTable::Open
- CTable.Open
helpviewer_keywords:
- CTable class
- Open method
ms.assetid: f13fdaa3-e198-4557-977d-54b0bbc3454d
ms.openlocfilehash: 47c9899889bbbf9b09300779691085786db0e088
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211151"
---
# <a name="ctable-class"></a>CTable (Clase)

Proporciona un medio para tener acceso directamente a un conjunto de filas simple (uno sin parámetros).

## <a name="syntax"></a>Sintaxis

```cpp
template <class TAccessor = CNoAccessor,
            template <typename T> class TRowset = CRowset>
class CTable :
   public CAccessorRowset <TAccessor, TRowset>
```

### <a name="parameters"></a>Parámetros

*TAccessor*<br/>
Una clase de descriptor de acceso.

*TRowset*<br/>
Una clase de conjunto de filas.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[Abrir](#open)|Abre la tabla.|

## <a name="remarks"></a>Observaciones

Vea [CCommand](../../data/oledb/ccommand-class.md) para obtener información sobre cómo ejecutar un comando para tener acceso a un conjunto de filas.

## <a name="ctableopen"></a><a name="open"></a>CTable:: Open

Abre la tabla.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT Open(const CSession& session,
   LPCWSTR wszTableName,
   DBPROPSET* pPropSet = NULL,
   ULONG ulPropSets = 0) throw ();

HRESULT Open(const CSession& session,
   LPCSTR szTableName,
   DBPROPSET* pPropSet = NULL,
   ULONG ulPropSets = 0) throw ();

HRESULT Open(const CSession& session,
   DBID& dbid,
   DBPROPSET* pPropSet = NULL,
   ULONG ulPropSets = 0) throw ();
```

#### <a name="parameters"></a>Parámetros

*sesión*<br/>
de Sesión para la que se abre la tabla.

*wszTableName*<br/>
de Nombre de la tabla que se va a abrir, pasado como una cadena Unicode.

*szTableName*<br/>
de Nombre de la tabla que se va a abrir, pasado como una cadena ANSI.

*dbid*<br/>
de `DBID` de la tabla que se va a abrir.

*pPropSet*<br/>
de Puntero a una matriz de estructuras [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) que contiene las propiedades y los valores que se van a establecer. Vea [conjuntos de propiedades y grupos de propiedades](/previous-versions/windows/desktop/ms713696(v=vs.85)) en la *Referencia del programador de OLE DB* en el Windows SDK. El valor predeterminado de NULL no especifica ninguna propiedad.

*ulPropSets*<br/>
de El número de estructuras [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) pasadas en el argumento *pPropSet* .

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [IOpenRowset:: OPENROWSET](/previous-versions/windows/desktop/ms716724(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
