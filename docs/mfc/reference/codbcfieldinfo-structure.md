---
title: CODBCFieldInfo (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CODBCFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- ODBC, data source information
- CODBCFieldInfo structure
ms.assetid: 92598b4f-facc-4108-b282-63a179ff79ab
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 1080eb323c599014d84acab94aee4622795fdb96
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

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
 `m_strName`  
 Nombre del campo.  
  
 *m_nSQLType*  
 El tipo de datos SQL del campo. Esto puede ser un tipo de datos SQL de ODBC o un tipo de datos SQL específicas del controlador. Para obtener una lista de tipos de datos de ODBC SQL válidos, vea "Tipos de datos de SQL" en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Para obtener información acerca de los tipos de datos SQL específico del controlador, consulte la documentación del controlador.  
  
 *m_nPrecision*  
 La precisión máxima del campo. Para obtener más información, vea "Precisión, escala, longitud y tamaño de presentación" en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 *m_nScale*  
 La escala del campo. Para obtener más información, vea "Precisión, escala, longitud y tamaño de presentación" en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 *m_nNullability*  
 Si el campo acepta un valor Null. Puede ser uno de dos valores: **SQL_NULLABLE** si el campo acepta valores Null, o **SQL_NO_NULLS** si el campo no acepta valores Null.  
  
## <a name="remarks"></a>Comentarios  
 Para recuperar esta información, llame a [CRecordset::GetODBCFieldInfo](../../mfc/reference/crecordset-class.md#getodbcfieldinfo).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRecordset::GetODBCFieldInfo](../../mfc/reference/crecordset-class.md#getodbcfieldinfo)   
 [CRecordset:: GetFieldValue](../../mfc/reference/crecordset-class.md#getfieldvalue)



