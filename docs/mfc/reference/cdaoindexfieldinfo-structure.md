---
title: CDaoIndexFieldInfo (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDaoIndexFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoIndexFieldInfo structure
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
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
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 975b3a704936adc9d4205938bb2c757ab650f0d9
ms.lasthandoff: 02/24/2017

---
# <a name="cdaoindexfieldinfo-structure"></a>CDaoIndexFieldInfo (Estructura)
El `CDaoIndexFieldInfo` estructura contiene información sobre un objeto de campo de índice definido para objetos de acceso a datos (DAO).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct CDaoIndexFieldInfo  
{  
    CString m_strName;          // Primary  
    BOOL m_bDescending;         // Primary  
};  
```  
  
#### <a name="parameters"></a>Parámetros  
 `m_strName`  
 Nombres de forma exclusiva el objeto de campo de índice. Para obtener más información, vea el tema "Nombre de propiedad" en la Ayuda de DAO.  
  
 *m_bDescending*  
 Indica el orden de índice definido por el objeto de índice. **TRUE** si es descendente.  
  
## <a name="remarks"></a>Comentarios  
 Un objeto de índice puede tener un número de campos, que indican qué campos se indiza una definición de tabla (o un conjunto de registros basado en una tabla) en. Las referencias a principal anterior indican cómo se devuelve la información en el `m_pFieldInfos` miembro de un [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) objeto obtenido mediante una llamada a la `GetIndexInfo` función miembro de clase [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo).  
  
 Objetos de índice y los objetos de campo de índice no se representan mediante una clase MFC. En su lugar, los objetos DAO subyacentes objetos MFC de la clase [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) contiene una colección de objetos index, llamado a la colección de índices. Cada objeto de índice, a su vez, contiene una colección de objetos de campo. Estas clases proporcionan funciones de miembro para tener acceso a elementos individuales de la información de índice, o puede tener acceso a ellos a la vez con un `CDaoIndexInfo` objeto mediante una llamada a la `GetIndexInfo` función de miembro del objeto contenedor. El `CDaoIndexInfo` objeto, a continuación, tiene un miembro de datos `m_pFieldInfos`, que apunta a una matriz de `CDaoIndexFieldInfo` objetos.  
  
 Llame a la `GetIndexInfo` función miembro del objeto contenedor tabledef o recordset en cuyos índices colección está almacenado el objeto de índice que le interese. A continuación, obtener acceso a la `m_pFieldInfos` miembro de la [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) objeto. La longitud de la `m_pFieldInfos` matriz se almacena en `m_nFields`. `CDaoIndexFieldInfo`También define un `Dump` se basa en la función miembro en modo de depuración. Puede usar `Dump` para volcar el contenido de una `CDaoIndexFieldInfo` objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)   
 [CDaoRecordset::GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)


