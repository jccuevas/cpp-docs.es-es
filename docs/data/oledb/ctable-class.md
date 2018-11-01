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
ms.openlocfilehash: 15081173edfae5ba0f881a6c1607a22e77a8a7c0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452174"
---
# <a name="ctable-class"></a>CTable (Clase)

Proporciona un medio para tener acceso directamente a un conjunto de filas sencillo (uno sin parámetros).

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

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[Abrir](#open)|Se abre en la tabla.|

## <a name="remarks"></a>Comentarios

Consulte [CCommand](../../data/oledb/ccommand-class.md) para obtener información sobre cómo ejecutar un comando para obtener acceso a un conjunto de filas.

## <a name="open"></a> CTable:: Open

Se abre en la tabla.

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

*Sesión*<br/>
[in] La sesión para el que se abre en la tabla.

*wszTableName*<br/>
[in] El nombre de la tabla para poder abrirlos, se pasa como una cadena Unicode.

*szTableName*<br/>
[in] El nombre de la tabla para poder abrirlos, se pasa como una cadena ANSI.

*dbid*<br/>
[in] El `DBID` de la tabla que desea abrir.

*pPropSet*<br/>
[in] Un puntero a una matriz de [DBPROPSET](/previous-versions/windows/desktop/ms714367) estructuras que contienen las propiedades y valores que desea establecer. Consulte [conjuntos de propiedades y grupos de propiedades](/previous-versions/windows/desktop/ms713696) en el *referencia del programador OLE DB* en el SDK de Windows. El valor predeterminado es null, especifica ninguna propiedad.

*ulPropSets*<br/>
[in] El número de [DBPROPSET](/previous-versions/windows/desktop/ms714367) pasan las estructuras en el *pPropSet* argumento.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [IOpenRowset:: OpenRowset](/previous-versions/windows/desktop/ms716724) en el *referencia del programador de OLE DB*.

## <a name="see-also"></a>Vea también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)