---
title: CDaoIndexFieldInfo (Estructura)
ms.date: 09/17/2019
f1_keywords:
- CDaoIndexFieldInfo
helpviewer_keywords:
- CDaoIndexFieldInfo structure [MFC]
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
ms.openlocfilehash: a8b0ff991b8cc4988192b89d7f70309af9b9112a
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096092"
---
# <a name="cdaoindexfieldinfo-structure"></a>CDaoIndexFieldInfo (Estructura)

La `CDaoIndexFieldInfo` estructura contiene información sobre un objeto de campo de índice definido para los objetos de acceso a datos (DAO).

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

Un objeto index puede tener varios campos, que indican los campos en los que se indiza una definición de tipo (o un conjunto de registros basado en una tabla). Las referencias a la principal anterior indican cómo se devuelve la información en `m_pFieldInfos` el miembro de un objeto [cdaoindexinfo (](../../mfc/reference/cdaoindexinfo-structure.md) obtenido mediante una `GetIndexInfo` llamada a la función miembro de la clase [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo).

Los objetos de índice y los objetos de campo de índice no se representan mediante una clase MFC. En su lugar, los objetos DAO subyacentes a objetos MFC de la clase [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) o [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) contienen una colección de objetos index, denominada colección Indexes. Cada objeto de índice, a su vez, contiene una colección de objetos de campo. Estas clases proporcionan funciones miembro para tener acceso a elementos individuales de información de índice, o bien se puede tener acceso a `CDaoIndexInfo` ellas todas a la `GetIndexInfo` vez con un objeto llamando a la función miembro del objeto contenedor. El `CDaoIndexInfo` objeto, a continuación, tiene un miembro de `m_pFieldInfos`datos,, que apunta a una `CDaoIndexFieldInfo` matriz de objetos.

Llame a `GetIndexInfo` la función miembro del objeto TableDef o Recordset contenedor en cuya colección Indexes esté almacenada el objeto de índice que le interese. A continuación, `m_pFieldInfos` acceda al miembro del objeto [cdaoindexinfo (](../../mfc/reference/cdaoindexinfo-structure.md) . La longitud de la `m_pFieldInfos` matriz se almacena en `m_nFields`. `CDaoIndexFieldInfo`también define una `Dump` función miembro en las compilaciones de depuración. Puede usar `Dump` para volcar el contenido de un `CDaoIndexFieldInfo` objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao. h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)<br/>
[CDaoRecordset::GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)
