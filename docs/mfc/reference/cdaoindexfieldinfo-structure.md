---
title: CDaoIndexFieldInfo (Estructura)
ms.date: 11/04/2016
f1_keywords:
- CDaoIndexFieldInfo
helpviewer_keywords:
- CDaoIndexFieldInfo structure [MFC]
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
ms.openlocfilehash: d03a6f6eadd4cf6ccb5279edf18675605d0b1485
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304280"
---
# <a name="cdaoindexfieldinfo-structure"></a>CDaoIndexFieldInfo (Estructura)

El `CDaoIndexFieldInfo` estructura contiene información sobre un objeto de campo de índice definido para los objetos de acceso a datos (DAO).

## <a name="syntax"></a>Sintaxis

```
struct CDaoIndexFieldInfo
{
    CString m_strName;          // Primary
    BOOL m_bDescending;         // Primary
};
```

#### <a name="parameters"></a>Parámetros

*m_strName*<br/>
Nombres de forma exclusiva el objeto de campo de índice. Para obtener más información, vea el tema "Nombre de la propiedad" en la Ayuda de DAO.

*m_bDescending*<br/>
Indica el orden de índice definido por el objeto de índice. TRUE si el orden es descendente.

## <a name="remarks"></a>Comentarios

Un objeto de índice puede tener un número de campos, que indica qué campos se indiza en a una definición de tabla (o un conjunto de registros basada en una tabla). Las referencias al elemento principal anterior indican cómo se devuelve la información en el `m_pFieldInfos` miembro de un [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) objeto obtenido mediante una llamada a la `GetIndexInfo` función miembro de clase [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo).

Objetos de índice y los objetos de campo de índice no están representados por una clase MFC. En su lugar, DAO objetos objetos MFC subyacentes de la clase [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) contienen una colección de objetos de índice, llama a la colección de índices. Cada objeto de índice, a su vez, contiene una colección de objetos de campo. Estas clases proporcionan funciones de miembro para tener acceso a elementos individuales de la información de índice, o puede tener acceso a ellos a la vez con un `CDaoIndexInfo` objeto mediante una llamada a la `GetIndexInfo` función de miembro del objeto contenedor. El `CDaoIndexInfo` objeto, a continuación, tiene un miembro de datos, `m_pFieldInfos`, que señala a una matriz de `CDaoIndexFieldInfo` objetos.

Llame a la `GetIndexInfo` función de miembro del objeto contenedor definición de tabla o conjunto de registros en cuyos índices colección está almacenado el objeto de índice que está interesado en. A continuación, obtener acceso a la `m_pFieldInfos` miembro de la [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) objeto. La longitud de la `m_pFieldInfos` matriz se almacena en `m_nFields`. `CDaoIndexFieldInfo` También define un `Dump` se basa en función de miembro en modo de depuración. Puede usar `Dump` para volcar el contenido de un `CDaoIndexFieldInfo` objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)<br/>
[CDaoRecordset::GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)
