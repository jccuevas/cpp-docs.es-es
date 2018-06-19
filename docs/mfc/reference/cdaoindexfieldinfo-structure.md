---
title: CDaoIndexFieldInfo (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoIndexFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoIndexFieldInfo structure [MFC]
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7be9a6a9db842f1e80be62f48a9990cff36168e5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33367261"
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
 Identifica inequívocamente el objeto de campo de índice. Para obtener más información, vea el tema "Nombre de propiedad" en la Ayuda de DAO.  
  
 *m_bDescending*  
 Indica el orden de índice definido por el objeto de índice. **TRUE** si el orden es descendente.  
  
## <a name="remarks"></a>Comentarios  
 Un objeto de índice puede tener un número de campos, que indica qué campos se indiza a una definición de tabla (o un conjunto de registros basado en una tabla) en. Las referencias al elemento principal anterior indican cómo se devuelve la información en el `m_pFieldInfos` miembro de un [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) objeto obtenido mediante una llamada a la `GetIndexInfo` función miembro de clase [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo).  
  
 Objetos de índice y objetos de campo de índice no están representados por una clase de MFC. En su lugar, DAO objetos objetos MFC subyacentes de la clase [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) contienen una colección de objetos de índice, llamado a la colección de índices. Cada objeto de índice, a su vez, contiene una colección de objetos de campo. Estas clases proporcionan funciones de miembro para tener acceso a elementos individuales de la información de índice, o puede tener acceso a ellos a la vez con un `CDaoIndexInfo` objeto mediante una llamada a la `GetIndexInfo` función de miembro del objeto contenedor. El `CDaoIndexInfo` objeto, a continuación, tiene un miembro de datos, `m_pFieldInfos`, que señala a una matriz de `CDaoIndexFieldInfo` objetos.  
  
 Llame a la `GetIndexInfo` función de miembro del objeto contenedor tabledef o conjunto de registros en cuyos índices es colección almacena el objeto de índice que le interesen. A continuación, obtener acceso a la `m_pFieldInfos` miembro de la [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) objeto. La longitud de la `m_pFieldInfos` matriz se almacena en `m_nFields`. `CDaoIndexFieldInfo` También define un `Dump` compila la función miembro en versiones de depuración. Puede usar `Dump` para volcar el contenido de un `CDaoIndexFieldInfo` objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)   
 [CDaoRecordset::GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)

