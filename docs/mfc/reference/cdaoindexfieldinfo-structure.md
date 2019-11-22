---
title: CDaoIndexFieldInfo (Estructura)
ms.date: 09/17/2019
f1_keywords:
- CDaoIndexFieldInfo
helpviewer_keywords:
- CDaoIndexFieldInfo structure [MFC]
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
ms.openlocfilehash: 10c786ef4fed9ecb3bbbb93526cd68a11e18d58c
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303665"
---
# <a name="cdaoindexfieldinfo-structure"></a>CDaoIndexFieldInfo (Estructura)

La estructura `CDaoIndexFieldInfo` contiene información sobre un objeto de campo de índice definido para objetos de acceso a datos (DAO).

DAO es compatible con Office 2013. DAO 3,6 es la versión final y se considera obsoleta.

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
Designa de forma única el objeto de campo de índice. Para obtener más información, vea el tema "propiedad Name" en la ayuda de DAO.

*m_bDescending*<br/>
Indica el orden de índice definido por el objeto de índice. TRUE si el orden es descendente.

## <a name="remarks"></a>Comentarios

Un objeto index puede tener varios campos, que indican los campos en los que se indiza una definición de tipo (o un conjunto de registros basado en una tabla). Las referencias a la principal anterior indican cómo se devuelve la información en el `m_pFieldInfos` miembro de un objeto [cdaoindexinfo (](../../mfc/reference/cdaoindexinfo-structure.md) obtenido mediante una llamada a la función miembro `GetIndexInfo` de la clase [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo).

Los objetos de índice y los objetos de campo de índice no se representan mediante una clase MFC. En su lugar, los objetos DAO subyacentes a objetos MFC de la clase [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) contienen una colección de objetos index, denominada colección Indexes. Cada objeto de índice, a su vez, contiene una colección de objetos de campo. Estas clases proporcionan funciones miembro para tener acceso a elementos individuales de información de índice, o bien se puede tener acceso a ellas todas a la vez con un objeto `CDaoIndexInfo` llamando a la función miembro `GetIndexInfo` del objeto contenedor. El objeto `CDaoIndexInfo`, a continuación, tiene un miembro de datos, `m_pFieldInfos`, que apunta a una matriz de objetos `CDaoIndexFieldInfo`.

Llame a la función miembro `GetIndexInfo` del objeto TableDef o Recordset contenedor en cuya colección Indexes esté almacenada el objeto de índice que le interese. A continuación, acceda al miembro `m_pFieldInfos` del objeto [cdaoindexinfo (](../../mfc/reference/cdaoindexinfo-structure.md) . La longitud de la matriz de `m_pFieldInfos` se almacena en `m_nFields`. `CDaoIndexFieldInfo` también define una función miembro de `Dump` en las compilaciones de depuración. Puede usar `Dump` para volcar el contenido de un objeto `CDaoIndexFieldInfo`.

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao. h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)<br/>
[CDaoRecordset::GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)
