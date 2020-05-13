---
title: CRestrictions (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL::CRestrictions
- CRestrictions
- ATL.CRestrictions
- CRestrictions.Open
- ATL::CRestrictions::Open
- ATL.CRestrictions.Open
- CRestrictions::Open
helpviewer_keywords:
- CRestrictions class
- Open method
ms.assetid: 0aaa2364-641c-4318-b110-7446aada4b4f
ms.openlocfilehash: 4a4c86987ceff0f04986d32011ba941e0d2319fe
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211307"
---
# <a name="crestrictions-class"></a>CRestrictions (Clase)

Una clase genérica que permite especificar restricciones para los conjuntos de filas de esquema.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T, short nRestrictions, const GUID* pguid>
class CRestrictions :
   public CSchemaRowset <T, nRestrictions>
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Clase utilizada para el descriptor de acceso.

*nRestrictions*<br/>
El número de columnas de restricción para el conjunto de filas de esquema.

*pguid*<br/>
Puntero al GUID del esquema.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbsch. h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[Abrir](#open)|Devuelve un conjunto de resultados según las restricciones proporcionadas por el usuario.|

## <a name="crestrictionsopen"></a><a name="open"></a>CRestrictions:: Open

Devuelve un conjunto de resultados según las restricciones proporcionadas por el usuario.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT Open(const CSession& session,
   LPCTSTR lpszParam 1 = NULL,
   LPCTSTR lpszParam 2 = NULL,
   LPCTSTR lpszParam 3 = NULL,
   LPCTSTR lpszParam 4 = NULL,
   LPCTSTR lpszParam 5 = NULL,
   LPCTSTR lpszParam 6 = NULL,
   LPCTSTR lpszParam 7 = NULL,
   bool bBind = true);
```

#### <a name="parameters"></a>Parámetros

*sesión*<br/>
de Especifica un objeto de sesión existente que se utiliza para conectarse al origen de datos.

*lpszParam*<br/>
de Especifica las restricciones en el conjunto de filas de esquema.

*bBind*<br/>
de Especifica si se debe enlazar el mapa de columnas automáticamente. El valor predeterminado es **true**, que hace que el mapa de columnas se enlace automáticamente. Si se establece *bBind* en **false** , se impide el enlace automático del mapa de columnas para que se pueda enlazar manualmente. (El enlace manual es de especial interés para los usuarios de OLAP).

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

Puede especificar un máximo de siete restricciones en un conjunto de filas de esquema.

Vea [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) para obtener información sobre las restricciones definidas en cada conjunto de filas de esquema.

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Clases de conjunto de filas de esquema y clases typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)
