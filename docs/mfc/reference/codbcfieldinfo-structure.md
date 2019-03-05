---
title: CODBCFieldInfo (Estructura)
ms.date: 11/04/2016
f1_keywords:
- CODBCFieldInfo
helpviewer_keywords:
- ODBC [MFC], data source information
- CODBCFieldInfo structure [MFC]
ms.assetid: 92598b4f-facc-4108-b282-63a179ff79ab
ms.openlocfilehash: bc2ad0c8319a60b773211dbd6b52b57bb2dbcafb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272768"
---
# <a name="codbcfieldinfo-structure"></a>CODBCFieldInfo (Estructura)

El `CODBCFieldInfo` estructura contiene información sobre los campos de un origen de datos ODBC.

## <a name="syntax"></a>Sintaxis

```
struct CODBCFieldInfo
{
    CString m_strName;
    SWORD m_nSQLType;
    UDWORD m_nPrecision;
    SWORD m_nScale;
    SWORD m_nNullability;
};
```

#### <a name="parameters"></a>Parámetros

*m_strName*<br/>
Nombre del campo.

*m_nSQLType*<br/>
El tipo de datos SQL del campo. Esto puede ser un tipo de datos SQL de ODBC o un tipo de datos SQL específicas del controlador. Para obtener una lista de tipos de datos ODBC SQL válidos, vea "Tipos de datos de SQL" en el SDK de Windows. Para obtener información acerca de los tipos de datos SQL específicas del controlador, consulte la documentación del controlador.

*m_nPrecision*<br/>
La precisión máxima del campo. Para obtener más información, vea "Precisión, escala, longitud y tamaño de presentación" en el SDK de Windows.

*m_nScale*<br/>
La escala del campo. Para obtener más información, vea "Precisión, escala, longitud y tamaño de presentación" en el SDK de Windows.

*m_nNullability*<br/>
Si el campo acepta un valor Null. Esto puede ser uno de dos valores: SQL_NULLABLE si el campo acepta valores Null o SQL_NO_NULLS si el campo no acepta valores Null.

## <a name="remarks"></a>Comentarios

Para recuperar esta información, llame al [CRecordset::GetODBCFieldInfo](../../mfc/reference/crecordset-class.md#getodbcfieldinfo).

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdb.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CRecordset::GetODBCFieldInfo](../../mfc/reference/crecordset-class.md#getodbcfieldinfo)<br/>
[CRecordset::GetFieldValue](../../mfc/reference/crecordset-class.md#getfieldvalue)
