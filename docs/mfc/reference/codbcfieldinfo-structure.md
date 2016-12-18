---
title: "CODBCFieldInfo (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CODBCFieldInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CODBCFieldInfo (estructura)"
  - "ODBC, información de origen de datos"
ms.assetid: 92598b4f-facc-4108-b282-63a179ff79ab
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CODBCFieldInfo (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `CODBCFieldInfo` contiene información sobre los campos en un origen de datos ODBC.  
  
## Sintaxis  
  
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
  
#### Parámetros  
 `m_strName`  
 Nombre del campo.  
  
 *m\_nSQLType*  
 El tipo de datos SQL de campo.  Esto puede ser un tipo de datos SQL de ODBC o un tipo de datos de SQL controlador\- concreto.  Para obtener una lista de tipos de datos SQL válidos de ODBC, vea “tipos de datos SQL” en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  Para obtener información sobre los tipos de datos SQL controlador\- concretos, vea la documentación del controlador.  
  
 *m\_nPrecision*  
 Precisión máxima del campo.  Para obtener información detallada, vea “Precisión, escala, Longitud, y el tamaño de la pantalla” en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 *m\_nScale*  
 La escala del campo.  Para obtener información detallada, vea “Precisión, escala, Longitud, y el tamaño de la pantalla” en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 *m\_nNullability*  
 Si el campo acepta un valor NULL.  Puede ser uno de dos valores: **SQL\_NULLABLE** si el campo acepta valores NULL, o **SQL\_NO\_NULLS** si el campo no acepta valores NULL.  
  
## Comentarios  
 Para recuperar esta información, llame a [CRecordset::GetODBCFieldInfo](../Topic/CRecordset::GetODBCFieldInfo.md).  
  
## Requisitos  
 **Encabezado:** afxdb.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRecordset::GetODBCFieldInfo](../Topic/CRecordset::GetODBCFieldInfo.md)   
 [CRecordset::GetFieldValue](../Topic/CRecordset::GetFieldValue.md)