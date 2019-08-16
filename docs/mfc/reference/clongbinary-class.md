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
ms.openlocfilehash: 94666c0d15898e05ae78663a15d86b7d00d5c9c6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505671"
---
# <a name="clongbinary-class"></a>CLongBinary (clase)

Simplifica el trabajo con objetos de datos binarios de gran tamaño (a menudo denominados BLOB, u "objetos binarios grandes") en una base de datos.

## <a name="syntax"></a>Sintaxis

```
class CLongBinary : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CLongBinary::CLongBinary](#clongbinary)|Construye un objeto `CLongBinary`.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CLongBinary::m_dwDataLength](#m_dwdatalength)|Contiene el tamaño real en bytes del objeto de datos cuyo identificador se almacena en `m_hData`.|
|[CLongBinary::m_hData](#m_hdata)|Contiene un identificador HGLOBAL de Windows para el objeto de imagen real.|

## <a name="remarks"></a>Comentarios

Por ejemplo, un campo de registro de una tabla SQL puede contener un mapa de bits que representa una imagen. Un `CLongBinary` objeto almacena un objeto de este tipo y realiza un seguimiento de su tamaño.

> [!NOTE]
>  En general, se recomienda usar [CByteArray](../../mfc/reference/cbytearray-class.md) junto con la función [DFX_Binary](record-field-exchange-functions.md#dfx_binary) . Todavía puede usar `CLongBinary`, pero en general `CByteArray` proporciona más funcionalidad en Win32, ya que ya no se encuentra la limitación de tamaño con 16 bits `CByteArray`. Este Consejo se aplica a la programación con objetos de acceso a datos (DAO) y con conectividad abierta de bases de datos (ODBC).

Para usar un `CLongBinary` objeto, declare un miembro de datos de `CLongBinary` campo de tipo en la clase de conjunto de registros. Este miembro será un miembro incrustado de la clase de conjunto de registros y se construirá cuando se construya el conjunto de registros. Una vez `CLongBinary` construido el objeto, el mecanismo de intercambio de campos de registros (RFX) carga el objeto de datos de un campo del registro actual en el origen de datos y lo almacena de nuevo en el registro cuando se actualiza el registro. RFX consulta el origen de datos para el tamaño del objeto binario grande, asigna almacenamiento para él (a través del `CLongBinary` miembro de `m_hData` datos del objeto) y almacena un `HGLOBAL` identificador para los datos en `m_hData`. RFX también almacena el tamaño real del objeto de datos en el `m_dwDataLength` miembro de datos. Trabaje con los datos del objeto a través `m_hData`de utilizando las mismas técnicas que usaría normalmente para manipular los datos almacenados en un identificador de Windows `HGLOBAL` .

Al destruir el conjunto de registros, el `CLongBinary` objeto incrustado también se destruye y su Destructor desasigna el `HGLOBAL` identificador de datos.

Para obtener más información sobre los objetos grandes y el `CLongBinary`uso de, vea los artículos [conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md) y [conjunto de registros: Trabajar con elementos de datos de gran tamaño](../../data/odbc/recordset-working-with-large-data-items-odbc.md)(ODBC).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CLongBinary`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdb_. h

##  <a name="clongbinary"></a>  CLongBinary::CLongBinary

Construye un objeto `CLongBinary`.

```
CLongBinary();
```

##  <a name="m_dwdatalength"></a>  CLongBinary::m_dwDataLength

Almacena el tamaño real en bytes de los datos almacenados en el identificador HGLOBAL en `m_hData`.

```
SQLULEN m_dwDataLength;
```

### <a name="remarks"></a>Comentarios

Este tamaño puede ser menor que el tamaño del bloque de memoria asignado para los datos. Llame a la función [GLobalSize](/windows/win32/api/winbase/nf-winbase-globalsize) de Win32 para obtener el tamaño asignado.

##  <a name="m_hdata"></a>CLongBinary:: m_hData

Almacena un identificador HGLOBAL de Windows en los datos de objetos binarios grandes reales.

```
HGLOBAL m_hData;
```

## <a name="see-also"></a>Vea también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CRecordset (clase)](../../mfc/reference/crecordset-class.md)
