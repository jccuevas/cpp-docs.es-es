---
title: CODBCFieldInfo (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CODBCFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- ODBC [MFC], data source information
- CODBCFieldInfo structure [MFC]
ms.assetid: 92598b4f-facc-4108-b282-63a179ff79ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5f178791bdaf57e5678f2e30d8994c2ffd140ffc
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055802"
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
[CRecordset:: GetFieldValue](../../mfc/reference/crecordset-class.md#getfieldvalue)

