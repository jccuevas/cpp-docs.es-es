---
title: CODBCFieldInfo (estructura) | Documentos de Microsoft
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
ms.openlocfilehash: ede515f0b8bc95d454fec48c6c6bd2109c43ce74
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040199"
---
# <a name="codbcfieldinfo-structure"></a>CODBCFieldInfo (Estructura)
El `CODBCFieldInfo` estructura contiene información acerca de los campos en un origen de datos ODBC.  
  
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
 *m_strName*  
 Nombre del campo.  
  
 *m_nSQLType*  
 El tipo de datos SQL del campo. Puede tratarse de un tipo de datos SQL de ODBC o un tipo de datos SQL específico del controlador. Para obtener una lista de tipos de datos de ODBC SQL válidos, vea "Tipos de datos de SQL" en el SDK de Windows. Para obtener información acerca de los tipos de datos SQL específico del controlador, consulte la documentación del controlador.  
  
 *m_nPrecision*  
 La precisión máxima del campo. Para obtener más información, vea "Precisión, escala, longitud y tamaño de presentación" en el SDK de Windows.  
  
 *m_nScale*  
 La escala del campo. Para obtener más información, vea "Precisión, escala, longitud y tamaño de presentación" en el SDK de Windows.  
  
 *m_nNullability*  
 Si el campo acepta un valor Null. Esto puede ser uno de dos valores: **SQL_NULLABLE** si el campo acepta valores Null, o **SQL_NO_NULLS** si el campo no acepta valores Null.  
  
## <a name="remarks"></a>Comentarios  
 Para resolver este problema, llame a [CRecordset::GetODBCFieldInfo](../../mfc/reference/crecordset-class.md#getodbcfieldinfo).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRecordset::GetODBCFieldInfo](../../mfc/reference/crecordset-class.md#getodbcfieldinfo)   
 [CRecordset:: GetFieldValue](../../mfc/reference/crecordset-class.md#getfieldvalue)


