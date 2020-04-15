---
title: CLongBinary (clase)
ms.date: 11/04/2016
f1_keywords:
- CLongBinary
- AFXDB_/CLongBinary
- AFXDB_/CLongBinary::CLongBinary
- AFXDB_/CLongBinary::m_dwDataLength
- AFXDB_/CLongBinary::m_hData
helpviewer_keywords:
- CLongBinary class [MFC]
ms.assetid: f4320059-aeb4-4ee5-bc2b-25f19d898ef5
ms.openlocfilehash: 1ce1daba90f3a1dad4b9627082d63f1b3405eab4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370135"
---
# <a name="clongbinary-class"></a>CLongBinary (clase)

Simplifica el trabajo con objetos de datos binarios de gran tamaño (a menudo denominados BLOB, u "objetos binarios grandes") en una base de datos.

## <a name="syntax"></a>Sintaxis

```
class CLongBinary : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CLongBinary::CLongBinary](#clongbinary)|Construye un objeto `CLongBinary`.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CLongBinary::m_dwDataLength](#m_dwdatalength)|Contiene el tamaño real en bytes del objeto `m_hData`de datos cuyo identificador se almacena en .|
|[CLongBinary::m_hData](#m_hdata)|Contiene un identificador HGLOBAL de Windows para el objeto de imagen real.|

## <a name="remarks"></a>Observaciones

Por ejemplo, un campo de registro en una tabla SQL puede contener un mapa de bits que representa una imagen. Un `CLongBinary` objeto almacena un objeto de este tipo y realiza un seguimiento de su tamaño.

> [!NOTE]
> En general, ahora es mejor usar [CByteArray](../../mfc/reference/cbytearray-class.md) junto con la función [DFX_Binary.](record-field-exchange-functions.md#dfx_binary) Todavía puede `CLongBinary`usar , `CByteArray` pero en general proporciona más funcionalidad en Win32, ya que `CByteArray`ya no hay la limitación de tamaño encontrada con 16 bits. Este consejo se aplica a la programación con objetos de acceso a datos (DAO) así como open Database Connectivity (ODBC).

Para utilizar `CLongBinary` un objeto, declare un `CLongBinary` miembro de datos de campo de tipo en la clase de conjunto de registros. Este miembro será un miembro incrustado de la clase de conjunto de registros y se construirá cuando se construya el conjunto de registros. Una `CLongBinary` vez construido el objeto, el mecanismo de intercambio de campos de registros (RFX) carga el objeto de datos desde un campo del registro actual en el origen de datos y lo almacena de nuevo en el registro cuando se actualiza el registro. RFX consulta el origen de datos para el tamaño del objeto binario `CLongBinary` grande, `m_hData` asigna almacenamiento para `HGLOBAL` él (a `m_hData`través del miembro de datos del objeto) y almacena un identificador a los datos en . RFX también almacena el tamaño real `m_dwDataLength` del objeto de datos en el miembro de datos. Trabajar con los datos `m_hData`del objeto a través de , utilizando las `HGLOBAL` mismas técnicas que normalmente usaría para manipular los datos almacenados en un identificador de Windows.

Al destruir el conjunto de `CLongBinary` registros, también se destruye el `HGLOBAL` objeto incrustado y su destructor desasigna el identificador de datos.

Para obtener más información acerca `CLongBinary`de los objetos grandes y el uso de , vea los artículos [Recordset (ODBC)](../../data/odbc/recordset-odbc.md) y [Recordset: Working with Large Data Items (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CLongBinary`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdb_.h

## <a name="clongbinaryclongbinary"></a><a name="clongbinary"></a>CLongBinary::CLongBinary

Construye un objeto `CLongBinary`.

```
CLongBinary();
```

## <a name="clongbinarym_dwdatalength"></a><a name="m_dwdatalength"></a>CLongBinary::m_dwDataLength

Almacena el tamaño real en bytes de los `m_hData`datos almacenados en el identificador HGLOBAL en .

```
SQLULEN m_dwDataLength;
```

### <a name="remarks"></a>Observaciones

Este tamaño puede ser menor que el tamaño del bloque de memoria asignado para los datos. Llame a la función Win32 [GLobalSize](/windows/win32/api/winbase/nf-winbase-globalsize) para obtener el tamaño asignado.

## <a name="clongbinarym_hdata"></a><a name="m_hdata"></a>CLongBinary::m_hData

Almacena un identificador HGLOBAL de Windows en los datos de objetos binarios grandes reales.

```
HGLOBAL m_hData;
```

## <a name="see-also"></a>Consulte también

[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CRecordset](../../mfc/reference/crecordset-class.md)
